---
title: "Porady: dodawanie lub usuwanie pozycji listy kontroli dostępu"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 16038ffbe090cfd8d2c0578f75e66db3b021cb9c
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
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
