---
title: 'Sposób: Dodawanie lub usuwanie wpisów listy kontroli dostępu (tylko net framework)'
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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "75708131"
---
# <a name="how-to-add-or-remove-access-control-list-entries-net-framework-only"></a>Sposób: Dodawanie lub usuwanie wpisów listy kontroli dostępu (tylko net framework)
Aby dodać lub usunąć wpisy listy kontroli dostępu (ACL) do <xref:System.Security.AccessControl.FileSecurity> lub <xref:System.Security.AccessControl.DirectorySecurity> z pliku lub katalogu, pobierz obiekt lub obiekt z pliku lub katalogu. Zmodyfikuj obiekt, a następnie zastosuj go z powrotem do pliku lub katalogu.  
  
## <a name="add-or-remove-an-acl-entry-from-a-file"></a>Dodawanie lub usuwanie wpisu acl z pliku  
  
1. Wywołaj <xref:System.IO.File.GetAccessControl%2A?displayProperty=nameWithType> metodę, <xref:System.Security.AccessControl.FileSecurity> aby uzyskać obiekt, który zawiera bieżące wpisy acl pliku.  
  
2. Dodawanie lub usuwanie wpisów <xref:System.Security.AccessControl.FileSecurity> acl z obiektu zwróconego z kroku 1.  
  
3. Aby zastosować zmiany, <xref:System.Security.AccessControl.FileSecurity> przekaż obiekt <xref:System.IO.File.SetAccessControl%2A?displayProperty=nameWithType> do metody.  
  
## <a name="add-or-remove-an-acl-entry-from-a-directory"></a>Dodawanie lub usuwanie wpisu acl z katalogu  
  
1. Wywołaj <xref:System.IO.Directory.GetAccessControl%2A?displayProperty=nameWithType> metodę, <xref:System.Security.AccessControl.DirectorySecurity> aby uzyskać obiekt, który zawiera bieżące wpisy acl katalogu.  
  
2. Dodawanie lub usuwanie wpisów <xref:System.Security.AccessControl.DirectorySecurity> acl z obiektu zwróconego z kroku 1.  
  
3. Aby zastosować zmiany, <xref:System.Security.AccessControl.DirectorySecurity> przekaż obiekt <xref:System.IO.Directory.SetAccessControl%2A?displayProperty=nameWithType> do metody.  
  
## <a name="example"></a>Przykład  
 Aby uruchomić ten przykład, należy użyć prawidłowego konta użytkownika lub grupy. W przykładzie <xref:System.IO.File> użyto obiektu. Użyj tej samej <xref:System.IO.FileInfo>procedury <xref:System.IO.Directory>dla <xref:System.IO.DirectoryInfo> , i klas.

 [!code-csharp[IO.File.GetAccessControl-SetAccessControl#1](../../../samples/snippets/csharp/VS_Snippets_CLR/IO.File.GetAccessControl-SetAccessControl/CS/sample.cs#1)]
 [!code-vb[IO.File.GetAccessControl-SetAccessControl#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/IO.File.GetAccessControl-SetAccessControl/VB/sample.vb#1)]  
