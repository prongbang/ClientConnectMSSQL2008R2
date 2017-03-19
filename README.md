# Client Connect MS SQL Server 2008 R2 (VB.Net)

#### Video Tutorials ([>>Click Me<<](https://www.youtube.com/watch?v=ljega_1MiAs))
#### Source Code
```vb

Imports System.Data.SqlClient

Public Class Form1

    Dim Sqlcon As SqlConnection

    Private Sub Form1_Load(sender As Object, e As EventArgs) Handles MyBase.Load
        Dim sqlCnn As SqlConnection
        Dim sqlCmd As SqlCommand 
        Dim connectionString = "Data Source=192.168.56.101;Initial Catalog=testdatabase;User ID=sa;Password=Ex4prongbang;"
        Dim sql = "select * from member"

        sqlCnn = New SqlConnection(connectionString)

        Try
            sqlCnn.Open()
            Label1.Text = "Client Connected IP 192.168.56.101"
            sqlCmd = New SqlCommand(sql, sqlCnn)
            Dim sqlReader As SqlDataReader = sqlCmd.ExecuteReader() 
            While sqlReader.Read()
                ListBox1.Items.Add(sqlReader.Item(0) & "     " & sqlReader.Item(1) & "     " & sqlReader.Item(2) & "     " & sqlReader.Item(3))
            End While
            sqlReader.Close()
            sqlCmd.Dispose()
            sqlCnn.Close()
        Catch ex As Exception
            Label1.Text = "Can not open connection ! IP 192.168.56.101"
        End Try

        '#1.Config MSSQL on Server : http://web.synametrics.com/sqlexpressremote.htm
        '    STEP 1: Enabling TCP/IP 
        '    STEP 2: Configure TCP/IP   ใส้ TCP Port 1433 แทน 5171

        '#2. Connect to SQL Server from client : https://stackoverflow.com/questions/10789686/how-to-connect-to-sql-server-from-client
        '
        '

        '#VISUAL BASIC .NET tutorials : http://www.c-sharpcorner.com/1/277/visual-basic-net.aspx

    End Sub
End Class

```
