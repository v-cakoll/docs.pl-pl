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
ms.openlocfilehash: 484ba261f8e5c88f17b3eba3a354967e2350a621
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2018
ms.locfileid: "43875892"
---
# <a name="how-to-enumerate-stores-for-isolated-storage"></a>Porady: wykazywanie magazynów dla izolowanego magazynu
Można wyliczyć wszystkich izolowanych magazynów dla bieżącego użytkownika za pomocą <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetEnumerator%2A?displayProperty=nameWithType> metody statycznej. Ta metoda przyjmuje <xref:System.IO.IsolatedStorage.IsolatedStorageScope> wartości i zwraca <xref:System.IO.IsolatedStorage.IsolatedStorageFile> modułu wyliczającego. Aby wyliczyć magazynów, musisz mieć <xref:System.Security.Permissions.IsolatedStorageFilePermission> uprawnień, który określa <xref:System.Security.Permissions.IsolatedStorageContainment.AdministerIsolatedStorageByUser> wartość. Jeśli wywołasz <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetEnumerator%2A> metody z <xref:System.IO.IsolatedStorage.IsolatedStorageScope.User> wartości, zwraca tablicę <xref:System.IO.IsolatedStorage.IsolatedStorageFile> obiekty, które są zdefiniowane dla bieżącego użytkownika.  
  
## <a name="example"></a>Przykład  
 Poniższy przykładowy kod uzyskuje sklepu, która jest izolowany dla konkretnego użytkownika i zestawu, tworzy kilka plików i pobiera pliki przy użyciu <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetEnumerator%2A> metody.  
  
 [!code-csharp[Conceptual.IsolatedStorage#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source2.cs#2)]
 [!code-vb[Conceptual.IsolatedStorage#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source2.vb#2)]  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.IO.IsolatedStorage.IsolatedStorageFile>  
- [Wydzielona pamięć masowa](../../../docs/standard/io/isolated-storage.md)
