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
ms.openlocfilehash: 645c4ea76509bf488b62669f65e03d3690fd5a05
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59103834"
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
