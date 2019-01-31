---
title: 'Instrukcje: Dodawanie lub usuwanie pozycji listy kontroli dostępu (tylko program .NET Framework)'
ms.date: 01/14/2019
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- ACEs [.NET Framework]
- ACLs [.NET Framework]
- access control entries [.NET Framework]
- I/O [.NET Framework], access control list entries
- access control lists [.NET Framework]
ms.assetid: 53758b39-bd9b-4640-bb04-cad5ed8d0abf
author: mairaw
ms.author: mairaw
ms.openlocfilehash: ea1059f541d2449a1a2d5dca1644ce8d9a553e40
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/30/2019
ms.locfileid: "55283351"
---
# <a name="how-to-add-or-remove-access-control-list-entries-net-framework-only"></a>Instrukcje: Dodawanie lub usuwanie pozycji listy kontroli dostępu (tylko program .NET Framework)
Aby dodać lub usunąć wpisy listy kontroli dostępu (ACL) do lub z pliku lub katalogu, Uzyskaj <xref:System.Security.AccessControl.FileSecurity> lub <xref:System.Security.AccessControl.DirectorySecurity> obiekt z pliku lub katalogu. Zmodyfikuj obiekt, a następnie zastosować je do pliku lub katalogu.  
  
## <a name="add-or-remove-an-acl-entry-from-a-file"></a>Dodawanie lub usuwanie pozycji listy ACL z pliku  
  
1.  Wywołaj <xref:System.IO.File.GetAccessControl%2A?displayProperty=nameWithType> metodę, aby uzyskać <xref:System.Security.AccessControl.FileSecurity> obiekt, który zawiera bieżące wpisy listy ACL w pliku.  
  
2.  Dodawanie lub usuwanie pozycji listy ACL z <xref:System.Security.AccessControl.FileSecurity> obiekt zwrócony z kroku 1.  
  
3. Aby zastosować zmiany, należy przekazać <xref:System.Security.AccessControl.FileSecurity> obiekt <xref:System.IO.File.SetAccessControl%2A?displayProperty=nameWithType> metody.  
  
## <a name="add-or-remove-an-acl-entry-from-a-directory"></a>Dodawanie lub usuwanie pozycji listy ACL z katalogu  
  
1.  Wywołaj <xref:System.IO.Directory.GetAccessControl%2A?displayProperty=nameWithType> metodę, aby uzyskać <xref:System.Security.AccessControl.DirectorySecurity> obiekt, który zawiera bieżące wpisy listy ACL w katalogu.  
  
2.  Dodawanie lub usuwanie pozycji listy ACL z <xref:System.Security.AccessControl.DirectorySecurity> obiekt zwrócony z kroku 1.  
  
3.  Aby zastosować zmiany, należy przekazać <xref:System.Security.AccessControl.DirectorySecurity> obiekt <xref:System.IO.Directory.SetAccessControl%2A?displayProperty=nameWithType> metody.  
  
## <a name="example"></a>Przykład  
 Aby uruchomić ten przykład, należy użyć prawidłowe konto użytkownika lub grupy. W przykładzie użyto <xref:System.IO.File> obiektu. Użyj tej samej procedury, aby uzyskać <xref:System.IO.FileInfo>, <xref:System.IO.Directory>, i <xref:System.IO.DirectoryInfo> klasy.

 [!code-csharp[IO.File.GetAccessControl-SetAccessControl#1](../../../samples/snippets/csharp/VS_Snippets_CLR/IO.File.GetAccessControl-SetAccessControl/CS/sample.cs#1)]
 [!code-vb[IO.File.GetAccessControl-SetAccessControl#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/IO.File.GetAccessControl-SetAccessControl/VB/sample.vb#1)]  
  
