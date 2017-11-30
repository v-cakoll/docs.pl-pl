---
title: Wykonywanie operacji katalogu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: e60f542f-6271-495b-a9e4-48553481c2a3
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: f67f393dce518a76b80d91f7294ed19e9a0f411a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="performing-catalog-operations"></a>Wykonywanie operacji katalogu
Do wykonania polecenia, aby zmodyfikować bazy danych lub katalogu, takie jak wykonywanie instrukcji CREATE TABLE lub CREATE PROCEDURE utworzyć **polecenia** przy użyciu odpowiedniej instrukcji SQL i **połączenia** obiektu. Wykonaj polecenie z **ExecuteNonQuery** metody **polecenia** obiektu.  
  
 Poniższy przykład kodu tworzy procedurę przechowywaną w bazie danych programu Microsoft SQL Server.  
  
```vb  
' Assumes connection is a valid SqlConnection.  
Dim queryString As String = "CREATE PROCEDURE InsertCategory " & _  
    "@CategoryName nchar(15), " & _  
    "@Identity int OUT " & _  
    "AS " & _  
    "INSERT INTO Categories (CategoryName) VALUES(@CategoryName) " & _  
    "SET @Identity = @@Identity " & _  
    "RETURN @@ROWCOUNT"  
  
Dim command As SqlCommand = New SqlCommand(queryString, connection)  
command.ExecuteNonQuery()  
```  
  
```csharp  
// Assumes connection is a valid SqlConnection.  
string queryString = "CREATE PROCEDURE InsertCategory  " +   
    "@CategoryName nchar(15), " +  
    "@Identity int OUT " +  
    "AS " +   
    "INSERT INTO Categories (CategoryName) VALUES(@CategoryName) " +   
    "SET @Identity = @@Identity " +  
    "RETURN @@ROWCOUNT";  
  
SqlCommand command = new SqlCommand(queryString, connection);  
command.ExecuteNonQuery();  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Aby zmodyfikować danych za pomocą poleceń](../../../../docs/framework/data/adonet/using-commands-to-modify-data.md)  
 [Poleceń i parametrów](../../../../docs/framework/data/adonet/commands-and-parameters.md)  
 [ADO.NET zarządzanego dostawcy i zestawu danych w Centrum deweloperów](http://go.microsoft.com/fwlink/?LinkId=217917)
