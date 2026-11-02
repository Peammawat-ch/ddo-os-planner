<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Bosch | MPJDDOOS Planner Change Log Tracker</title>
  <style>
    /* ==========================================================================
       BOSCH DESIGN SYSTEM (FROK) VARIABLES & RESET
       ========================================================================== */
    :root {
      /* Bosch Corporate Colors */
      --bosch-red: #E20015;
      --bosch-red-dark: #B50011;
      --bosch-blue: #005691;
      --bosch-blue-hover: #003E6B;
      --bosch-light-blue: #008ECF;
      --bosch-turquoise: #00A8B0;
      --bosch-green: #00884A;
      --bosch-green-bg: #E6F4EE;
      --bosch-green-hover: #006D3B;

      /* Neutrals */
      --bosch-black: #000000;
      --bosch-gray-900: #212529;
      --bosch-gray-700: #525F6B;
      --bosch-gray-500: #71767C;
      --bosch-gray-300: #C1C7CC;
      --bosch-gray-200: #E0E2E5;
      --bosch-gray-100: #F4F5F6;
      --bosch-white: #FFFFFF;

      --font-family: "Bosch Sans", -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, Helvetica, Arial, sans-serif;
    }

    * {
      box-sizing: border-box;
      margin: 0;
      padding: 0;
    }

    body {
      font-family: var(--font-family);
      background-color: var(--bosch-gray-100);
      color: var(--bosch-gray-900);
      line-height: 1.5;
      min-height: 100vh;
      display: flex;
      flex-direction: column;
    }

    /* Bosch Signature Supergraphic Accent Line */
    .bosch-supergraphic {
      height: 8px;
      width: 100%;
      background: linear-gradient(
        90deg,
        #781D7D 0%,
        #E20015 20%,
        #005691 45%,
        #008ECF 70%,
        #00A8B0 85%,
        #00884A 100%
      );
    }

    /* Top Navigation Header */
    .app-header {
      background-color: var(--bosch-white);
      border-bottom: 1px solid var(--bosch-gray-200);
      padding: 14px 24px;
      position: sticky;
      top: 0;
      z-index: 100;
    }

    .header-container {
      max-width: 1400px;
      margin: 0 auto;
      display: flex;
      justify-content: space-between;
      align-items: center;
      flex-wrap: wrap;
      gap: 16px;
    }

    .brand-section {
      display: flex;
      align-items: center;
      gap: 18px;
    }

    /* Bosch Logo from user image */
    .bosch-logo-img {
      height: 38px;
      width: auto;
      max-width: 160px;
      object-fit: contain;
      display: block;
    }

    .divider-vertical {
      width: 1px;
      height: 32px;
      background-color: var(--bosch-gray-300);
    }

    .app-title-group h1 {
      font-size: 1.15rem;
      font-weight: 700;
      color: var(--bosch-gray-900);
      letter-spacing: -0.2px;
    }

    .app-title-group p {
      font-size: 0.8rem;
      color: var(--bosch-gray-700);
    }

    .header-links {
      display: flex;
      align-items: center;
      gap: 12px;
      flex-wrap: wrap;
    }

    /* Bosch Sharp Geometry Buttons */
    .btn {
      font-family: var(--font-family);
      font-size: 0.875rem;
      font-weight: 600;
      padding: 8px 16px;
      border-radius: 0; /* Bosch Strict 0px Border Radius */
      border: 1px solid transparent;
      cursor: pointer;
      display: inline-flex;
      align-items: center;
      justify-content: center;
      gap: 8px;
      text-decoration: none;
      transition: background-color 0.15s ease, color 0.15s ease, border-color 0.15s ease;
    }

    .btn-primary {
      background-color: var(--bosch-blue);
      color: var(--bosch-white);
    }

    .btn-primary:hover {
      background-color: var(--bosch-blue-hover);
    }

    .btn-secondary {
      background-color: var(--bosch-white);
      color: var(--bosch-blue);
      border-color: var(--bosch-blue);
    }

    .btn-secondary:hover {
      background-color: var(--bosch-gray-100);
    }

    /* ==========================================================================
       TOP DASHBOARD: NEW UPDATE COUNTER + UNIFIED SEARCH & FILTERS
       ========================================================================== */
    .main-container {
      max-width: 1400px;
      width: 100%;
      margin: 20px auto;
      padding: 0 24px;
      flex: 1;
    }

    .dashboard-topbar {
      background: var(--bosch-white);
      border: 1px solid var(--bosch-gray-200);
      border-left: 5px solid var(--bosch-red);
      padding: 16px 20px;
      margin-bottom: 20px;
      display: flex;
      align-items: center;
      justify-content: space-between;
      flex-wrap: wrap;
      gap: 16px;
      box-shadow: 0 1px 3px rgba(0,0,0,0.04);
    }

    /* Left Side: New Update Counter Display */
    .new-update-widget {
      display: flex;
      align-items: center;
      gap: 14px;
      padding-right: 20px;
      border-right: 1px solid var(--bosch-gray-200);
      min-width: 200px;
    }

    .new-update-badge {
      background-color: var(--bosch-red);
      color: var(--bosch-white);
      font-size: 1.5rem;
      font-weight: 800;
      min-width: 48px;
      height: 48px;
      display: flex;
      align-items: center;
      justify-content: center;
      padding: 0 10px;
      letter-spacing: -0.5px;
    }

    .new-update-label-group {
      display: flex;
      flex-direction: column;
    }

    .new-update-title {
      font-size: 0.82rem;
      font-weight: 800;
      text-transform: uppercase;
      letter-spacing: 0.6px;
      color: var(--bosch-gray-900);
    }

    .new-update-subtitle {
      font-size: 0.76rem;
      color: var(--bosch-gray-700);
    }

    /* Right Side: Search and Filters placed directly next to it */
    .topbar-controls {
      display: flex;
      align-items: flex-end;
      flex: 1;
      flex-wrap: wrap;
      gap: 14px;
    }

    .control-item {
      display: flex;
      flex-direction: column;
      gap: 4px;
    }

    .control-item.search-item {
      flex: 2;
      min-width: 220px;
    }

    .control-item.filter-item {
      flex: 1;
      min-width: 170px;
    }

    .control-label {
      font-size: 0.72rem;
      font-weight: 700;
      color: var(--bosch-gray-700);
      text-transform: uppercase;
      letter-spacing: 0.4px;
    }

    .form-control {
      font-family: var(--font-family);
      font-size: 0.875rem;
      padding: 8px 12px;
      border: 1px solid var(--bosch-gray-300);
      border-bottom: 2px solid var(--bosch-gray-700);
      background-color: var(--bosch-gray-100);
      color: var(--bosch-gray-900);
      border-radius: 0;
      outline: none;
      width: 100%;
      height: 38px;
      transition: border-color 0.15s ease, background-color 0.15s ease;
    }

    .form-control:focus {
      border-bottom-color: var(--bosch-blue);
      background-color: var(--bosch-white);
    }

    /* Status Notifications */
    .alert-banner {
      padding: 12px 16px;
      border-radius: 0;
      margin-bottom: 16px;
      display: none;
      font-size: 0.875rem;
      align-items: center;
      justify-content: space-between;
    }

    .alert-banner.active {
      display: flex;
    }

    .alert-warning {
      background-color: #FEF3C7;
      border-left: 4px solid #F59E0B;
      color: #92400E;
    }

    .alert-info {
      background-color: #EBF3F9;
      border-left: 4px solid var(--bosch-blue);
      color: var(--bosch-blue);
    }

    /* ==========================================================================
       DAILY CHANGE LOG TABLE
       ========================================================================== */
    .table-wrapper {
      background: var(--bosch-white);
      border: 1px solid var(--bosch-gray-200);
      overflow-x: auto;
      box-shadow: 0 1px 3px rgba(0,0,0,0.03);
    }

    table.bosch-table {
      width: 100%;
      border-collapse: collapse;
      text-align: left;
    }

    table.bosch-table thead th {
      background-color: var(--bosch-gray-200);
      color: var(--bosch-gray-900);
      font-size: 0.76rem;
      font-weight: 700;
      text-transform: uppercase;
      letter-spacing: 0.5px;
      padding: 12px 16px;
      border-bottom: 2px solid var(--bosch-gray-300);
      white-space: nowrap;
      user-select: none;
    }

    table.bosch-table thead th.sortable {
      cursor: pointer;
    }

    table.bosch-table thead th.sortable:hover {
      background-color: var(--bosch-gray-300);
    }

    /* Daily Group Row Header */
    .day-group-row td {
      background-color: #EBF3F9;
      color: var(--bosch-blue);
      font-weight: 700;
      font-size: 0.84rem;
      padding: 10px 16px;
      border-bottom: 1px solid var(--bosch-gray-300);
    }

    .day-group-header {
      display: flex;
      justify-content: space-between;
      align-items: center;
      flex-wrap: wrap;
      gap: 8px;
    }

    table.bosch-table tbody tr.ticket-row {
      border-bottom: 1px solid var(--bosch-gray-200);
      transition: background-color 0.12s ease;
    }

    table.bosch-table tbody tr.ticket-row:hover {
      background-color: var(--bosch-gray-100);
    }

    table.bosch-table tbody tr.ticket-row.row-checked {
      background-color: #FAFAFA;
      color: var(--bosch-gray-700);
    }

    table.bosch-table tbody td {
      padding: 14px 16px;
      font-size: 0.9rem;
      vertical-align: middle;
    }

    /* Badges */
    .badge {
      display: inline-flex;
      align-items: center;
      padding: 3px 10px;
      font-size: 0.74rem;
      font-weight: 700;
      text-transform: uppercase;
      letter-spacing: 0.3px;
      white-space: nowrap;
    }

    .badge-new-ticket {
      background-color: #E5F1FB;
      color: var(--bosch-blue);
      border-left: 3px solid var(--bosch-blue);
    }

    .badge-completed {
      background-color: var(--bosch-green-bg);
      color: var(--bosch-green);
      border-left: 3px solid var(--bosch-green);
    }

    .ticket-id {
      font-family: monospace;
      font-size: 0.8rem;
      color: var(--bosch-gray-700);
      font-weight: 600;
    }

    .ticket-title {
      font-weight: 700;
      color: var(--bosch-gray-900);
      margin-top: 1px;
    }

    .row-checked .ticket-title {
      color: var(--bosch-gray-700);
    }

    .change-summary-text {
      color: var(--bosch-gray-900);
      font-size: 0.88rem;
    }

    .ticket-link {
      color: var(--bosch-blue);
      font-weight: 600;
      text-decoration: none;
      display: inline-flex;
      align-items: center;
      gap: 4px;
      font-size: 0.85rem;
      white-space: nowrap;
    }

    .ticket-link:hover {
      text-decoration: underline;
      color: var(--bosch-blue-hover);
    }

    /* Reversible Status Button */
    .btn-status-toggle {
      min-width: 146px;
      padding: 6px 12px;
      font-size: 0.78rem;
      font-weight: 700;
      text-transform: uppercase;
      letter-spacing: 0.4px;
    }

    .btn-status-new {
      background-color: var(--bosch-blue);
      color: var(--bosch-white);
      border: 1px solid var(--bosch-blue);
    }

    .btn-status-new:hover {
      background-color: var(--bosch-blue-hover);
    }

    .btn-status-checked {
      background-color: var(--bosch-white);
      color: var(--bosch-green);
      border: 1px solid var(--bosch-green);
    }

    .btn-status-checked:hover {
      background-color: var(--bosch-green-bg);
    }

    .empty-state {
      text-align: center;
      padding: 56px 24px;
      color: var(--bosch-gray-700);
    }

    .empty-state h3 {
      font-size: 1.1rem;
      color: var(--bosch-gray-900);
      margin-bottom: 6px;
    }

    /* ==========================================================================
       RESPONSIVE DESIGN (MOBILE & TABLET)
       ========================================================================== */
    @media (max-width: 900px) {
      .dashboard-topbar {
        flex-direction: column;
        align-items: stretch;
      }

      .new-update-widget {
        border-right: none;
        border-bottom: 1px solid var(--bosch-gray-200);
        padding-bottom: 12px;
        padding-right: 0;
      }

      table.bosch-table thead {
        display: none;
      }

      table.bosch-table,
      table.bosch-table tbody,
      table.bosch-table tr.ticket-row,
      table.bosch-table td {
        display: block;
        width: 100%;
      }

      table.bosch-table tr.ticket-row {
        padding: 12px 16px;
        border-bottom: 2px solid var(--bosch-gray-200);
      }

      table.bosch-table tbody td {
        padding: 6px 0;
        display: flex;
        justify-content: space-between;
        align-items: center;
        text-align: right;
        gap: 12px;
      }

      table.bosch-table tbody td::before {
        content: attr(data-label);
        font-size: 0.74rem;
        font-weight: 700;
        text-transform: uppercase;
        color: var(--bosch-gray-700);
        text-align: left;
      }

      .ticket-title,
      .change-summary-text {
        text-align: right;
      }

      .btn-status-toggle {
        width: 100%;
        margin-top: 6px;
      }
    }

    .app-footer {
      background: var(--bosch-white);
      border-top: 1px solid var(--bosch-gray-200);
      padding: 16px 24px;
      font-size: 0.8rem;
      color: var(--bosch-gray-700);
      text-align: center;
      margin-top: auto;
    }
  </style>
</head>
<body>

  <!-- Bosch Signature Supergraphic Accent -->
  <div class="bosch-supergraphic"></div>

  <!-- Top App Navigation -->
  <header class="app-header">
    <div class="header-container">
      <div class="brand-section">
        <!-- Bosch Logo Image -->
        <img 
          src="Bosch logo.png" 
          alt="Bosch Logo" 
          class="bosch-logo-img" 
          onerror="this.onerror=null; this.outerHTML='<span style=\'font-weight:800; font-size:1.4rem; color:var(--bosch-red); letter-spacing:1px;\'>BOSCH</span>';"
        />
        <div class="divider-vertical"></div>
        <div class="app-title-group">
          <h1>MPJDDOOS Planner Change Tracker</h1>
          <p>Live Microsoft Planner Daily Updates &bull; SharePoint Database</p>
        </div>
      </div>

      <div class="header-links">
        <!-- Direct Planner Link -->
        <a 
          href="https://planner.cloud.microsoft/ui/web/plan/CjBUzW57r0Cki7JC-b9eF5YAGpsz/view/board?tid=0ae51e19-07c8-4e4b-bb6d-648ee58410f4" 
          target="_blank" 
          rel="noopener noreferrer" 
          class="btn btn-primary"
        >
          Open Plan in Planner &#8599;
        </a>
        <a 
          href="https://bosch.sharepoint.com/:l:/r/sites/msteams_70eb1052/Lists/MPJDDOOS%20Planner%20Change%20Log?e=EvmgDs" 
          target="_blank" 
          rel="noopener noreferrer" 
          class="btn btn-secondary"
        >
          SharePoint List &#8599;
        </a>
        <button class="btn btn-secondary" id="btnRefresh" title="Fetch latest updates from SharePoint">
          &#8635; Refresh
        </button>
      </div>
    </div>
  </header>

  <!-- Main Content Area -->
  <main class="main-container">

    <!-- Top Dashboard: New Update Counter + Unified Search & Filters -->
    <section class="dashboard-topbar" aria-label="Dashboard and Filters">
      <!-- Left: New Update Counter -->
      <div class="new-update-widget">
        <div class="new-update-badge" id="countNewUpdate">0</div>
        <div class="new-update-label-group">
          <span class="new-update-title">New Updates</span>
          <span class="new-update-subtitle" id="newUpdateSubtext">Awaiting your review</span>
        </div>
      </div>

      <!-- Right: Search Bar and Filters Next to It -->
      <div class="topbar-controls">
        <div class="control-item search-item">
          <label class="control-label" for="searchInput">Search Ticket / Change</label>
          <input 
            type="text" 
            id="searchInput" 
            class="form-control" 
            placeholder="Search by ticket title, ID, or what changed..."
          />
        </div>

        <div class="control-item filter-item">
          <label class="control-label" for="filterStatus">Acknowledge Status</label>
          <select id="filterStatus" class="form-control">
            <option value="ALL">All Updates</option>
            <option value="New Update" selected>New Update (Unchecked)</option>
            <option value="Checked">Checked (Acknowledged)</option>
          </select>
        </div>

        <div class="control-item filter-item">
          <label class="control-label" for="filterChangeType">Change Event</label>
          <select id="filterChangeType" class="form-control">
            <option value="ALL">All Events</option>
            <option value="New Ticket">New Ticket Created</option>
            <option value="Completed">Ticket Completed</option>
          </select>
        </div>

        <div class="control-item" style="min-width: 140px;">
          <label class="control-label" for="sortOrder">Sort Date</label>
          <select id="sortOrder" class="form-control">
            <option value="DESC">Newest First</option>
            <option value="ASC">Oldest First</option>
          </select>
        </div>
      </div>
    </section>

    <!-- Information / Notification Banner -->
    <div id="statusBanner" class="alert-banner alert-info">
      <span id="statusBannerText">Connecting to SharePoint database...</span>
    </div>

    <!-- Daily Changes Table -->
    <section class="table-wrapper">
      <table class="bosch-table" id="changeLogTable">
        <thead>
          <tr>
            <th class="sortable" id="thSortDate">Date &amp; Time &#8595;</th>
            <th>Ticket ID &amp; Title</th>
            <th>Change Type</th>
            <th>What Changed</th>
            <th>Original Ticket</th>
            <th>Review Status</th>
          </tr>
        </thead>
        <tbody id="tableBody">
          <!-- Populated purely from SharePoint database -->
        </tbody>
      </table>
    </section>

  </main>

  <!-- Footer -->
  <footer class="app-footer">
    &copy; Robert Bosch GmbH &bull; MPJDDOOS Microsoft Planner Daily Change Tracker &bull; Connected to SharePoint
  </footer>

  <!-- Core JavaScript & SharePoint Direct REST Integration -->
  <script>
    /***************************************************************************
     * CONFIGURATION & CONSTANTS
     ***************************************************************************/
    const CONFIG = {
      siteUrl: "https://bosch.sharepoint.com/sites/msteams_70eb1052",
      listName: "MPJDDOOS Planner Change Log",
      plannerBaseBoardUrl: "https://planner.cloud.microsoft/ui/web/plan/CjBUzW57r0Cki7JC-b9eF5YAGpsz/view/board?tid=0ae51e19-07c8-4e4b-bb6d-648ee58410f4"
    };

    // State management: No mock data
    let appState = {
      items: [],
      isLoading: false,
      searchQuery: "",
      statusFilter: "ALL",
      typeFilter: "ALL",
      sortDirection: "DESC"
    };

    /***************************************************************************
     * SHAREPOINT REST API INTEGRATION
     ***************************************************************************/
    async function fetchSharePointChanges() {
      appState.isLoading = true;
      showBanner("info", "Loading changes from SharePoint database...");
      renderTable();

      try {
        const endpoint = `${CONFIG.siteUrl}/_api/web/lists/getbytitle('${encodeURIComponent(CONFIG.listName)}')/items?$select=Id,Title,TicketID,ChangeType,ChangeSummary,ChangeDate,TicketLink,ReviewStatus&$orderby=ChangeDate desc`;

        const response = await fetch(endpoint, {
          method: "GET",
          headers: {
            "Accept": "application/json;odata=nometadata"
          },
          credentials: "include"
        });

        if (!response.ok) {
          throw new Error(`HTTP ${response.status}: ${response.statusText}`);
        }

        const data = await response.json();
        const records = Array.isArray(data.value) ? data.value : [];

        // Parse SharePoint records
        appState.items = records.map(row => {
          let link = CONFIG.plannerBaseBoardUrl;
          if (row.TicketLink) {
            link = typeof row.TicketLink === "object" && row.TicketLink.Url ? row.TicketLink.Url : row.TicketLink;
          }

          return {
            id: row.Id,
            ticketId: row.TicketID || `T-${row.Id}`,
            title: row.Title || "Untitled Ticket",
            changeType: row.ChangeType || "New Ticket",
            changeSummary: row.ChangeSummary || (row.ChangeType === "Completed" ? "Ticket marked as Completed" : "New ticket created in Planner"),
            changeDate: row.ChangeDate || new Date().toISOString(),
            ticketLink: link,
            reviewStatus: row.ReviewStatus || "New Update"
          };
        });

        hideBanner();
      } catch (err) {
        console.warn("Direct SharePoint list query encountered an error:", err);
        showBanner("warning", "Note: When testing on localhost outside Bosch SharePoint, ensure you are authenticated or access through Microsoft Edge with SharePoint credentials. Click 'SharePoint List ↗' in the header to view directly.");
        // App remains with 0 mock tickets, accurately displaying empty or offline state
        appState.items = [];
      } finally {
        appState.isLoading = false;
        renderTable();
      }
    }

    async function updateSharePointStatus(itemId, newStatus) {
      // 1. Optimistic UI update
      const item = appState.items.find(i => i.id === itemId);
      if (item) {
        item.reviewStatus = newStatus;
        renderTable();
      }

      // 2. Persist update back to SharePoint
      try {
        // Fetch Request Digest token
        const contextRes = await fetch(`${CONFIG.siteUrl}/_api/contextinfo`, {
          method: "POST",
          headers: { "Accept": "application/json;odata=nometadata" },
          credentials: "include"
        });

        if (contextRes.ok) {
          const contextData = await contextRes.json();
          const digest = contextData.FormDigestValue;

          await fetch(
            `${CONFIG.siteUrl}/_api/web/lists/getbytitle('${encodeURIComponent(CONFIG.listName)}')/items(${itemId})`,
            {
              method: "POST",
              headers: {
                "Accept": "application/json;odata=nometadata",
                "Content-Type": "application/json;odata=nometadata",
                "IF-MATCH": "*",
                "X-HTTP-Method": "MERGE",
                "X-RequestDigest": digest
              },
              credentials: "include",
              body: JSON.stringify({ ReviewStatus: newStatus })
            }
          );
        }
      } catch (e) {
        console.error("Could not write back to SharePoint:", e);
      }
    }

    function toggleStatus(itemId) {
      const item = appState.items.find(i => i.id === itemId);
      if (!item) return;
      const nextStatus = item.reviewStatus === "New Update" ? "Checked" : "New Update";
      updateSharePointStatus(itemId, nextStatus);
    }

    function markDayChecked(dateKey) {
      const targetItems = appState.items.filter(i => i.changeDate.slice(0, 10) === dateKey && i.reviewStatus === "New Update");
      targetItems.forEach(item => {
        updateSharePointStatus(item.id, "Checked");
      });
    }

    /***************************************************************************
     * RENDERING & FILTERING
     ***************************************************************************/
    function formatDayHeader(dateStr) {
      const dateObj = new Date(dateStr + "T00:00:00");
      return dateObj.toLocaleDateString("en-GB", {
        weekday: "long",
        day: "2-digit",
        month: "short",
        year: "numeric"
      });
    }

    function formatTimeOnly(isoString) {
      const d = new Date(isoString);
      return d.toLocaleTimeString("en-GB", { hour: "2-digit", minute: "2-digit" });
    }

    function renderTable() {
      // 1. Calculate New Update Counter for the Top Dashboard
      const unseenCount = appState.items.filter(i => i.reviewStatus === "New Update").length;
      document.getElementById("countNewUpdate").textContent = unseenCount;
      document.getElementById("newUpdateSubtext").textContent = 
        unseenCount === 0 ? "All caught up" : `${unseenCount} unacknowledged`;

      // 2. Filter records
      const query = appState.searchQuery.trim().toLowerCase();
      let filtered = appState.items.filter(item => {
        const matchesSearch =
          !query ||
          item.title.toLowerCase().includes(query) ||
          item.ticketId.toLowerCase().includes(query) ||
          item.changeSummary.toLowerCase().includes(query);

        const matchesStatus =
          appState.statusFilter === "ALL" || item.reviewStatus === appState.statusFilter;

        const matchesType =
          appState.typeFilter === "ALL" || item.changeType === appState.typeFilter;

        return matchesSearch && matchesStatus && matchesType;
      });

      // 3. Sort by Date
      filtered.sort((a, b) => {
        const tA = new Date(a.changeDate).getTime();
        const tB = new Date(b.changeDate).getTime();
        return appState.sortDirection === "DESC" ? tB - tA : tA - tB;
      });

      const tbody = document.getElementById("tableBody");
      tbody.innerHTML = "";

      // Loading State
      if (appState.isLoading) {
        tbody.innerHTML = `
          <tr>
            <td colspan="6" class="empty-state">
              <h3>Loading changes...</h3>
              <p>Fetching records from SharePoint list <em>${escapeHtml(CONFIG.listName)}</em>.</p>
            </td>
          </tr>
        `;
        return;
      }

      // Empty State (No records found)
      if (filtered.length === 0) {
        tbody.innerHTML = `
          <tr>
            <td colspan="6" class="empty-state">
              <h3>No ticket updates found</h3>
              <p>There are no change records matching your search or filter criteria in the SharePoint list.</p>
            </td>
          </tr>
        `;
        return;
      }

      // 4. Group by Day
      const groupedByDay = {};
      filtered.forEach(item => {
        const dayKey = item.changeDate.slice(0, 10);
        if (!groupedByDay[dayKey]) groupedByDay[dayKey] = [];
        groupedByDay[dayKey].push(item);
      });

      Object.keys(groupedByDay).forEach(dayKey => {
        const dayItems = groupedByDay[dayKey];
        const unseenInDay = dayItems.filter(i => i.reviewStatus === "New Update").length;

        // Render Day Header Banner
        const groupTr = document.createElement("tr");
        groupTr.className = "day-group-row";
        groupTr.innerHTML = `
          <td colspan="6">
            <div class="day-group-header">
              <span>&#128197; ${formatDayHeader(dayKey)} (${dayItems.length} update${dayItems.length > 1 ? "s" : ""})</span>
              ${
                unseenInDay > 0
                  ? `<button class="btn btn-secondary" style="padding: 3px 10px; font-size: 0.74rem;" onclick="markDayChecked('${dayKey}')">
                       Mark all ${unseenInDay} new on this day as Checked
                     </button>`
                  : `<span style="color: var(--bosch-green); font-size: 0.76rem;">&#10003; All updates acknowledged for this day</span>`
              }
            </div>
          </td>
        `;
        tbody.appendChild(groupTr);

        // Render Item Rows
        dayItems.forEach(item => {
          const isChecked = item.reviewStatus === "Checked";
          const badgeClass = item.changeType === "Completed" ? "badge-completed" : "badge-new-ticket";

          const tr = document.createElement("tr");
          tr.className = `ticket-row ${isChecked ? "row-checked" : ""}`;
          tr.innerHTML = `
            <td data-label="Date & Time">
              <div><strong>${item.changeDate.slice(0, 10)}</strong></div>
              <div style="font-size: 0.78rem; color: var(--bosch-gray-700);">${formatTimeOnly(item.changeDate)}</div>
            </td>
            <td data-label="Ticket">
              <div class="ticket-id">${escapeHtml(item.ticketId)}</div>
              <div class="ticket-title">${escapeHtml(item.title)}</div>
            </td>
            <td data-label="Change Type">
              <span class="badge ${badgeClass}">${escapeHtml(item.changeType)}</span>
            </td>
            <td data-label="What Changed">
              <div class="change-summary-text">${escapeHtml(item.changeSummary)}</div>
            </td>
            <td data-label="Original Ticket">
              <a href="${escapeHtml(item.ticketLink)}" target="_blank" rel="noopener noreferrer" class="ticket-link">
                Open in Planner &#8599;
              </a>
            </td>
            <td data-label="Review Status">
              <button 
                type="button" 
                class="btn btn-status-toggle ${isChecked ? "btn-status-checked" : "btn-status-new"}"
                onclick="toggleStatus(${item.id})"
                title="Click to change status"
              >
                ${isChecked ? "&#10003; Checked (Undo)" : "&#9679; New Update &rarr; Check"}
              </button>
            </td>
          `;
          tbody.appendChild(tr);
        });
      });
    }

    function showBanner(type, message) {
      const banner = document.getElementById("statusBanner");
      banner.className = `alert-banner alert-${type} active`;
      document.getElementById("statusBannerText").innerHTML = message;
    }

    function hideBanner() {
      document.getElementById("statusBanner").classList.remove("active");
    }

    function escapeHtml(str) {
      if (!str) return "";
      return String(str)
        .replace(/&/g, "&amp;")
        .replace(/</g, "&lt;")
        .replace(/>/g, "&gt;")
        .replace(/"/g, "&quot;");
    }

    /***************************************************************************
     * EVENT LISTENERS
     ***************************************************************************/
    document.getElementById("searchInput").addEventListener("input", e => {
      appState.searchQuery = e.target.value;
      renderTable();
    });

    document.getElementById("filterStatus").addEventListener("change", e => {
      appState.statusFilter = e.target.value;
      renderTable();
    });

    document.getElementById("filterChangeType").addEventListener("change", e => {
      appState.typeFilter = e.target.value;
      renderTable();
    });

    document.getElementById("sortOrder").addEventListener("change", e => {
      appState.sortDirection = e.target.value;
      renderTable();
    });

    document.getElementById("thSortDate").addEventListener("click", () => {
      appState.sortDirection = appState.sortDirection === "DESC" ? "ASC" : "DESC";
      document.getElementById("sortOrder").value = appState.sortDirection;
      renderTable();
    });

    document.getElementById("btnRefresh").addEventListener("click", () => {
      fetchSharePointChanges();
    });

    // Start fetching from SharePoint on page load
    fetchSharePointChanges();
  </script>
</body>
</html>
