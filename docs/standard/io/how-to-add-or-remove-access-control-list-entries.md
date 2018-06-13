---
title: 'Porady: dodawanie lub usuwanie pozycji listy kontroli dostępu'
ms.date: 03/30/2017
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
ms.openlocfilehash: 24c428a80f18b35d0aa3119a3c5fa1a6dcb2130e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33573426"
---
# <a name="how-to-add-or-remove-access-control-list-entries"></a>Porady: dodawanie lub usuwanie pozycji listy kontroli dostępu
Aby dodać lub usunąć wpisy listy kontroli dostępu (ACL) do lub z pliku, <xref:System.Security.AccessControl.FileSecurity> lub <xref:System.Security.AccessControl.DirectorySecurity> obiektu musi być uzyskane z pliku lub katalogu, modyfikować i następnie stosowane do pliku lub katalogu.  
  
### <a name="to-add-or-remove-an-acl-entry-from-a-file"></a>Aby dodać lub usunąć wpis listy ACL z pliku  
  
1.  Wywołanie <xref:System.IO.File.GetAccessControl%2A> metodę, aby pobrać <xref:System.Security.AccessControl.FileSecurity> obiekt, który zawiera bieżące wpisy list kontroli dostępu w pliku.  
  
2.  Dodawanie lub usuwanie pozycji listy ACL z <xref:System.Security.AccessControl.FileSecurity> obiekt zwrócony z kroku 1.  
  
3.  Przekaż <xref:System.Security.AccessControl.FileSecurity> do obiektu <xref:System.IO.File.SetAccessControl%2A> metody w celu zastosowania zmian.  
  
### <a name="to-add-or-remove-an-acl-entry-from-a-directory"></a>Aby dodać lub usunąć wpis listy ACL z katalogu  
  
1.  Wywołanie <xref:System.IO.Directory.GetAccessControl%2A> metodę, aby pobrać <xref:System.Security.AccessControl.DirectorySecurity> obiekt, który zawiera bieżące wpisy listy ACL w katalogu.  
  
2.  Dodawanie lub usuwanie pozycji listy ACL z <xref:System.Security.AccessControl.DirectorySecurity> obiekt zwrócony z kroku 1.  
  
3.  Przekaż <xref:System.Security.AccessControl.DirectorySecurity> do obiektu <xref:System.IO.Directory.SetAccessControl%2A> metody w celu zastosowania zmian.  
  
## <a name="example"></a>Przykład  
 [!code-cpp[IO.File.GetAccessControl-SetAccessControl#1](../../../samples/snippets/cpp/VS_Snippets_CLR/IO.File.GetAccessControl-SetAccessControl/cpp/sample.cpp#1)]
 [!code-csharp[IO.File.GetAccessControl-SetAccessControl#1](../../../samples/snippets/csharp/VS_Snippets_CLR/IO.File.GetAccessControl-SetAccessControl/CS/sample.cs#1)]
 [!code-vb[IO.File.GetAccessControl-SetAccessControl#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/IO.File.GetAccessControl-SetAccessControl/VB/sample.vb#1)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Należy podać prawidłowe konto użytkownika lub grupy do uruchomienia tego przykładu. W tym przykładzie użyto <xref:System.IO.File> obiektu; jednak służy do tej samej procedury <xref:System.IO.FileInfo>, <xref:System.IO.Directory>, i <xref:System.IO.DirectoryInfo> klasy.
