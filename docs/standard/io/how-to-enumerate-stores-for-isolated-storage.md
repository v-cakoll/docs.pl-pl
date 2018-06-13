---
title: 'Porady: wykazywanie magazynów dla izolowanego magazynu'
ms.date: 03/30/2017
ms.technology: dotnet-standard
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 77f6053cad85b5012a455a1fc020e0f559defdc9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33573766"
---
# <a name="how-to-enumerate-stores-for-isolated-storage"></a>Porady: wykazywanie magazynów dla izolowanego magazynu
Można wyliczyć wszystkich izolowanych magazynów dla bieżącego użytkownika przy użyciu <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetEnumerator%2A?displayProperty=nameWithType> metody statycznej. Ta metoda przyjmuje <xref:System.IO.IsolatedStorage.IsolatedStorageScope> wartości i zwraca <xref:System.IO.IsolatedStorage.IsolatedStorageFile> modułu wyliczającego. Aby wyliczyć magazynów, musisz mieć <xref:System.Security.Permissions.IsolatedStorageFilePermission> uprawnień, który określa <xref:System.Security.Permissions.IsolatedStorageContainment.AdministerIsolatedStorageByUser> wartość. Jeśli należy wywołać <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetEnumerator%2A> metody z <xref:System.IO.IsolatedStorage.IsolatedStorageScope.User> wartości, zwraca tablicę <xref:System.IO.IsolatedStorage.IsolatedStorageFile> obiektów, które są zdefiniowane dla bieżącego użytkownika.  
  
## <a name="example"></a>Przykład  
 Poniższy przykładowy kod uzyskuje sklepu, która jest izolowana przez użytkownika i zestawu, tworzy kilka plików i pobiera pliki przy użyciu <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetEnumerator%2A> metody.  
  
 [!code-csharp[Conceptual.IsolatedStorage#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source2.cs#2)]
 [!code-vb[Conceptual.IsolatedStorage#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source2.vb#2)]  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.IO.IsolatedStorage.IsolatedStorageFile>  
 [Wydzielona pamięć masowa](../../../docs/standard/io/isolated-storage.md)
