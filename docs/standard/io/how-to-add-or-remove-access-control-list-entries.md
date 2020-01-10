---
title: 'Instrukcje: Dodawanie lub usuwanie pozycji listy Access Control (tylko .NET Framework)'
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
ms.openlocfilehash: 5f41c518b8732adff95593cab29d7085adcc9ab3
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75708131"
---
# <a name="how-to-add-or-remove-access-control-list-entries-net-framework-only"></a>Instrukcje: Dodawanie lub usuwanie pozycji listy Access Control (tylko .NET Framework)
Aby dodać lub usunąć wpisy listy Access Control (ACL) do lub z pliku lub katalogu, Pobierz obiekt <xref:System.Security.AccessControl.FileSecurity> lub <xref:System.Security.AccessControl.DirectorySecurity> z pliku lub katalogu. Zmodyfikuj obiekt, a następnie Zastosuj go z powrotem do pliku lub katalogu.  
  
## <a name="add-or-remove-an-acl-entry-from-a-file"></a>Dodawanie lub usuwanie wpisu listy ACL z pliku  
  
1. Wywołaj metodę <xref:System.IO.File.GetAccessControl%2A?displayProperty=nameWithType>, aby uzyskać obiekt <xref:System.Security.AccessControl.FileSecurity> zawierający bieżące wpisy listy ACL pliku.  
  
2. Dodaj lub Usuń wpisy listy ACL z obiektu <xref:System.Security.AccessControl.FileSecurity> zwróconego z kroku 1.  
  
3. Aby zastosować zmiany, przekaż obiekt <xref:System.Security.AccessControl.FileSecurity> do metody <xref:System.IO.File.SetAccessControl%2A?displayProperty=nameWithType>.  
  
## <a name="add-or-remove-an-acl-entry-from-a-directory"></a>Dodawanie lub usuwanie wpisu listy ACL z katalogu  
  
1. Wywołaj metodę <xref:System.IO.Directory.GetAccessControl%2A?displayProperty=nameWithType>, aby uzyskać obiekt <xref:System.Security.AccessControl.DirectorySecurity> zawierający bieżące wpisy listy ACL katalogu.  
  
2. Dodaj lub Usuń wpisy listy ACL z obiektu <xref:System.Security.AccessControl.DirectorySecurity> zwróconego z kroku 1.  
  
3. Aby zastosować zmiany, przekaż obiekt <xref:System.Security.AccessControl.DirectorySecurity> do metody <xref:System.IO.Directory.SetAccessControl%2A?displayProperty=nameWithType>.  
  
## <a name="example"></a>Przykład  
 Do uruchomienia tego przykładu należy użyć prawidłowego konta użytkownika lub grupy. W przykładzie zastosowano obiekt <xref:System.IO.File>. Użyj tej samej procedury dla klas <xref:System.IO.FileInfo>, <xref:System.IO.Directory>i <xref:System.IO.DirectoryInfo>.

 [!code-csharp[IO.File.GetAccessControl-SetAccessControl#1](../../../samples/snippets/csharp/VS_Snippets_CLR/IO.File.GetAccessControl-SetAccessControl/CS/sample.cs#1)]
 [!code-vb[IO.File.GetAccessControl-SetAccessControl#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/IO.File.GetAccessControl-SetAccessControl/VB/sample.vb#1)]  
