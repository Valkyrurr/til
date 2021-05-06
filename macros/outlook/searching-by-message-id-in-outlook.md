```vba
Private Sub Application_AdvancedSearchComplete(ByVal SearchObject As Search)
    If SearchObject.Tag = "MessageId" Then
        Set Results = SearchObject.Results
        MsgBox "Message-ID search complete. " & Results.Count & " result(s) found."
        For i = 1 To Results.Count
            Results.Item(i).Display
        Next
    End If
End Sub

Public Sub SearchMessageId()
    Set Folder = Session.PickFolder
    If Not Folder Is Nothing Then
        r = MsgBox("Include subfolders?", vbYesNoCancel, "Search by Message-ID")
        If r <> vbCancel Then
            MessageId = InputBox("Message-ID:")
            If MessageId <> "" Then
                Application.AdvancedSearch "'" & Folder.FolderPath & "'", "http://schemas.microsoft.com/mapi/proptag/0x1035001F = '" & MessageId & "'", r = vbYes, "MessageId"
            End If
        End If
    End If
End Sub
```

Reference: https://itectec.com/superuser/searching-by-message-id-in-outlook/
