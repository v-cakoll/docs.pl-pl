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
ms.openlocfilehash: 3ba38093e9e978c89cdb2bb7a584ed9e04c1096d
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75707531"
---
# <a name="how-to-enumerate-stores-for-isolated-storage"></a>Porady: wykazywanie magazynów dla izolowanego magazynu
Wszystkie magazyny izolowane dla bieżącego użytkownika można wyliczyć przy użyciu metody statycznej <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetEnumerator%2A?displayProperty=nameWithType>. Ta metoda przyjmuje wartość <xref:System.IO.IsolatedStorage.IsolatedStorageScope> i zwraca moduł wyliczający <xref:System.IO.IsolatedStorage.IsolatedStorageFile>. Aby wyliczyć magazyny, musisz mieć uprawnienie <xref:System.Security.Permissions.IsolatedStorageFilePermission>, które określa <xref:System.Security.Permissions.IsolatedStorageContainment.AdministerIsolatedStorageByUser> wartość. Jeśli wywołasz metodę <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetEnumerator%2A> z wartością <xref:System.IO.IsolatedStorage.IsolatedStorageScope.User>, zwróci ona tablicę <xref:System.IO.IsolatedStorage.IsolatedStorageFile> obiektów, które są zdefiniowane dla bieżącego użytkownika.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kodu uzyskuje magazyn izolowany przez użytkownika i zestaw, tworzy kilka plików i pobiera te pliki przy użyciu metody <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetEnumerator%2A>.  
  
 [!code-csharp[Conceptual.IsolatedStorage#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source2.cs#2)]
 [!code-vb[Conceptual.IsolatedStorage#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source2.vb#2)]  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.IO.IsolatedStorage.IsolatedStorageFile>
- [Wydzielona pamięć masowa](../../../docs/standard/io/isolated-storage.md)
