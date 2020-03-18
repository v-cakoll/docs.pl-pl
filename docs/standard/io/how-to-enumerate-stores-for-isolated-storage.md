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
# <a name="how-to-enumerate-stores-for-isolated-storage"></a><span data-ttu-id="d52c9-102">Porady: wykazywanie magazynów dla izolowanego magazynu</span><span class="sxs-lookup"><span data-stu-id="d52c9-102">How to: Enumerate Stores for Isolated Storage</span></span>
<span data-ttu-id="d52c9-103">Można wyliczyć wszystkie izolowane magazyny dla <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetEnumerator%2A?displayProperty=nameWithType> bieżącego użytkownika przy użyciu metody statycznej.</span><span class="sxs-lookup"><span data-stu-id="d52c9-103">You can enumerate all isolated stores for the current user by using the  <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetEnumerator%2A?displayProperty=nameWithType> static method.</span></span> <span data-ttu-id="d52c9-104">Ta metoda <xref:System.IO.IsolatedStorage.IsolatedStorageScope> przyjmuje wartość <xref:System.IO.IsolatedStorage.IsolatedStorageFile> i zwraca wyliczacz.</span><span class="sxs-lookup"><span data-stu-id="d52c9-104">This  method takes an <xref:System.IO.IsolatedStorage.IsolatedStorageScope> value and returns an <xref:System.IO.IsolatedStorage.IsolatedStorageFile> enumerator.</span></span> <span data-ttu-id="d52c9-105">Aby wyliczyć magazyny, musisz <xref:System.Security.Permissions.IsolatedStorageFilePermission> mieć uprawnienie, które określa <xref:System.Security.Permissions.IsolatedStorageContainment.AdministerIsolatedStorageByUser> wartość.</span><span class="sxs-lookup"><span data-stu-id="d52c9-105">To enumerate stores, you must have the <xref:System.Security.Permissions.IsolatedStorageFilePermission> permission that specifies the <xref:System.Security.Permissions.IsolatedStorageContainment.AdministerIsolatedStorageByUser> value.</span></span> <span data-ttu-id="d52c9-106">Jeśli wywołasz <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetEnumerator%2A> metodę <xref:System.IO.IsolatedStorage.IsolatedStorageScope.User> z wartością, <xref:System.IO.IsolatedStorage.IsolatedStorageFile> zwraca tablicę obiektów, które są zdefiniowane dla bieżącego użytkownika.</span><span class="sxs-lookup"><span data-stu-id="d52c9-106">If you call the <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetEnumerator%2A> method with the <xref:System.IO.IsolatedStorage.IsolatedStorageScope.User> value, it returns an array of <xref:System.IO.IsolatedStorage.IsolatedStorageFile> objects that are defined for the current user.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d52c9-107">Przykład</span><span class="sxs-lookup"><span data-stu-id="d52c9-107">Example</span></span>  
 <span data-ttu-id="d52c9-108">Poniższy przykład kodu uzyskuje magazyn, który jest izolowany przez użytkownika i zestawu, tworzy <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetEnumerator%2A> kilka plików i pobiera te pliki przy użyciu metody.</span><span class="sxs-lookup"><span data-stu-id="d52c9-108">The following code example obtains a store that is isolated by user and assembly, creates a few files, and retrieves those files by using the <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetEnumerator%2A> method.</span></span>  
  
 [!code-csharp[Conceptual.IsolatedStorage#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source2.cs#2)]
 [!code-vb[Conceptual.IsolatedStorage#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source2.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="d52c9-109">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d52c9-109">See also</span></span>

- <xref:System.IO.IsolatedStorage.IsolatedStorageFile>
- [<span data-ttu-id="d52c9-110">Izolowany magazyn</span><span class="sxs-lookup"><span data-stu-id="d52c9-110">Isolated Storage</span></span>](../../../docs/standard/io/isolated-storage.md)
