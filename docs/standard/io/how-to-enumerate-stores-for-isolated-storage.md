---
title: "Porady: wykazywanie magazynów dla izolowanego magazynu"
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
helpviewer_keywords:
- enumerating stores
- data storage using isolated storage, enumerating stores
- storing data using isolated storage, enumerating stores
- stores, enumerating
- isolated storage, enumerating stores
- data stores, enumerating
ms.assetid: 0fcf279a-f241-48f0-8034-2e3d331f1fcb
caps.latest.revision: "13"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 8f8863f1d8b3c7f4ed8f65f8f8eb3e8af51b0405
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-enumerate-stores-for-isolated-storage"></a>Porady: wykazywanie magazynów dla izolowanego magazynu
Można wyliczyć wszystkich izolowanych magazynów dla bieżącego użytkownika przy użyciu <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetEnumerator%2A?displayProperty=nameWithType> metody statycznej. Ta metoda przyjmuje <xref:System.IO.IsolatedStorage.IsolatedStorageScope> wartości i zwraca <xref:System.IO.IsolatedStorage.IsolatedStorageFile> modułu wyliczającego. Aby wyliczyć magazynów, musisz mieć <xref:System.Security.Permissions.IsolatedStorageFilePermission> uprawnień, który określa <xref:System.Security.Permissions.IsolatedStorageContainment.AdministerIsolatedStorageByUser> wartość. Jeśli należy wywołać <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetEnumerator%2A> metody z <xref:System.IO.IsolatedStorage.IsolatedStorageScope.User> wartości, zwraca tablicę <xref:System.IO.IsolatedStorage.IsolatedStorageFile> obiektów, które są zdefiniowane dla bieżącego użytkownika.  
  
## <a name="example"></a>Przykład  
 Poniższy przykładowy kod uzyskuje sklepu, która jest izolowana przez użytkownika i zestawu, tworzy kilka plików i pobiera pliki przy użyciu <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetEnumerator%2A> metody.  
  
 [!code-csharp[Conceptual.IsolatedStorage#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source2.cs#2)]
 [!code-vb[Conceptual.IsolatedStorage#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source2.vb#2)]  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.IO.IsolatedStorage.IsolatedStorageFile>  
 [Izolowany Magazyn](../../../docs/standard/io/isolated-storage.md)
