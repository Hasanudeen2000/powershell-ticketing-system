# powershell-ticketing-system
A basic ticket system using PowerShell and a CSV file

**# Steps:**

1. Open PowerShell.

2. Create a CSV file for tickets:
"TicketID,User,Issue,Status" | Out-File -FilePath "C:\Tickets\tickets.csv"

3. Add a new ticket:
"1,Alice,Printer not working,Open" | Out-File -FilePath "C:\Tickets\tickets.csv" -Append

4. Open CSV file in C drive to check tickets

5. Update ticket to "Completed":
$Tickets = Import-Csv -Path "C:\Tickets\tickets.csv"

foreach ($Ticket in $Tickets) {
    if ($Ticket.User -eq "Alice") {
        $Ticket.Status = "Completed"
    }
}

$Tickets | Export-Csv -Path "C:\Tickets\tickets.csv" -NoTypeInformation

6. Delete all completed tickets:
$Tickets = Import-Csv -Path "C:\Tickets\tickets.csv"

$ActiveTickets = $Tickets | Where-Object { $_.Status -ne "Completed" }

$ActiveTickets | Export-Csv -Path "C:\Tickets\tickets.csv" -NoTypeInformation

**Screenshots:**
<img width="947" alt="ps1" src="https://github.com/user-attachments/assets/c687cf2f-4103-40c8-abeb-94d93ab21a6e" />
<img width="947" alt="ps2" src="https://github.com/user-attachments/assets/4725af47-d73f-4719-b5be-05517cb55aba" />
<img width="960" alt="EXCEL_1YIsntINzE" src="https://github.com/user-attachments/assets/95cafaa5-0d07-4aea-b80a-fb7361ae6811" />

