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
# <a name="how-to-enumerate-stores-for-isolated-storage"></a><span data-ttu-id="99fb6-102">Porady: wykazywanie magazynów dla izolowanego magazynu</span><span class="sxs-lookup"><span data-stu-id="99fb6-102">How to: Enumerate Stores for Isolated Storage</span></span>
<span data-ttu-id="99fb6-103">Można wyliczyć wszystkich izolowanych magazynów dla bieżącego użytkownika przy użyciu <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetEnumerator%2A?displayProperty=nameWithType> metody statycznej.</span><span class="sxs-lookup"><span data-stu-id="99fb6-103">You can enumerate all isolated stores for the current user by using the  <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetEnumerator%2A?displayProperty=nameWithType> static method.</span></span> <span data-ttu-id="99fb6-104">Ta metoda przyjmuje <xref:System.IO.IsolatedStorage.IsolatedStorageScope> wartości i zwraca <xref:System.IO.IsolatedStorage.IsolatedStorageFile> modułu wyliczającego.</span><span class="sxs-lookup"><span data-stu-id="99fb6-104">This  method takes an <xref:System.IO.IsolatedStorage.IsolatedStorageScope> value and returns an <xref:System.IO.IsolatedStorage.IsolatedStorageFile> enumerator.</span></span> <span data-ttu-id="99fb6-105">Aby wyliczyć magazynów, musisz mieć <xref:System.Security.Permissions.IsolatedStorageFilePermission> uprawnień, który określa <xref:System.Security.Permissions.IsolatedStorageContainment.AdministerIsolatedStorageByUser> wartość.</span><span class="sxs-lookup"><span data-stu-id="99fb6-105">To enumerate stores, you must have the <xref:System.Security.Permissions.IsolatedStorageFilePermission> permission that specifies the <xref:System.Security.Permissions.IsolatedStorageContainment.AdministerIsolatedStorageByUser> value.</span></span> <span data-ttu-id="99fb6-106">Jeśli należy wywołać <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetEnumerator%2A> metody z <xref:System.IO.IsolatedStorage.IsolatedStorageScope.User> wartości, zwraca tablicę <xref:System.IO.IsolatedStorage.IsolatedStorageFile> obiektów, które są zdefiniowane dla bieżącego użytkownika.</span><span class="sxs-lookup"><span data-stu-id="99fb6-106">If you call the <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetEnumerator%2A> method with the <xref:System.IO.IsolatedStorage.IsolatedStorageScope.User> value, it returns an array of <xref:System.IO.IsolatedStorage.IsolatedStorageFile> objects that are defined for the current user.</span></span>  
  
## <a name="example"></a><span data-ttu-id="99fb6-107">Przykład</span><span class="sxs-lookup"><span data-stu-id="99fb6-107">Example</span></span>  
 <span data-ttu-id="99fb6-108">Poniższy przykładowy kod uzyskuje sklepu, która jest izolowana przez użytkownika i zestawu, tworzy kilka plików i pobiera pliki przy użyciu <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetEnumerator%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="99fb6-108">The following code example obtains a store that is isolated by user and assembly, creates a few files, and retrieves those files by using the <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetEnumerator%2A> method.</span></span>  
  
 [!code-csharp[Conceptual.IsolatedStorage#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source2.cs#2)]
 [!code-vb[Conceptual.IsolatedStorage#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source2.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="99fb6-109">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="99fb6-109">See Also</span></span>  
 <xref:System.IO.IsolatedStorage.IsolatedStorageFile>  
 [<span data-ttu-id="99fb6-110">Wydzielona pamięć masowa</span><span class="sxs-lookup"><span data-stu-id="99fb6-110">Isolated Storage</span></span>](../../../docs/standard/io/isolated-storage.md)
