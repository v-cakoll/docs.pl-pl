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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "75707531"
---
# <a name="how-to-enumerate-stores-for-isolated-storage"></a>Porady: wykazywanie magazynów dla izolowanego magazynu
Można wyliczyć wszystkie izolowane magazyny dla <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetEnumerator%2A?displayProperty=nameWithType> bieżącego użytkownika przy użyciu metody statycznej. Ta metoda <xref:System.IO.IsolatedStorage.IsolatedStorageScope> przyjmuje wartość <xref:System.IO.IsolatedStorage.IsolatedStorageFile> i zwraca wyliczacz. Aby wyliczyć magazyny, musisz <xref:System.Security.Permissions.IsolatedStorageFilePermission> mieć uprawnienie, które określa <xref:System.Security.Permissions.IsolatedStorageContainment.AdministerIsolatedStorageByUser> wartość. Jeśli wywołasz <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetEnumerator%2A> metodę <xref:System.IO.IsolatedStorage.IsolatedStorageScope.User> z wartością, <xref:System.IO.IsolatedStorage.IsolatedStorageFile> zwraca tablicę obiektów, które są zdefiniowane dla bieżącego użytkownika.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kodu uzyskuje magazyn, który jest izolowany przez użytkownika i zestawu, tworzy <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetEnumerator%2A> kilka plików i pobiera te pliki przy użyciu metody.  
  
 [!code-csharp[Conceptual.IsolatedStorage#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source2.cs#2)]
 [!code-vb[Conceptual.IsolatedStorage#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source2.vb#2)]  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.IO.IsolatedStorage.IsolatedStorageFile>
- [Izolowany magazyn](../../../docs/standard/io/isolated-storage.md)
