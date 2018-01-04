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
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 7c4fa63c5c7f966831a55c9103c9ba58cfa621d6
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/23/2017
---
# <a name="how-to-enumerate-stores-for-isolated-storage"></a><span data-ttu-id="9bc8e-102">Porady: wykazywanie magazynów dla izolowanego magazynu</span><span class="sxs-lookup"><span data-stu-id="9bc8e-102">How to: Enumerate Stores for Isolated Storage</span></span>
<span data-ttu-id="9bc8e-103">Można wyliczyć wszystkich izolowanych magazynów dla bieżącego użytkownika przy użyciu <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetEnumerator%2A?displayProperty=nameWithType> metody statycznej.</span><span class="sxs-lookup"><span data-stu-id="9bc8e-103">You can enumerate all isolated stores for the current user by using the  <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetEnumerator%2A?displayProperty=nameWithType> static method.</span></span> <span data-ttu-id="9bc8e-104">Ta metoda przyjmuje <xref:System.IO.IsolatedStorage.IsolatedStorageScope> wartości i zwraca <xref:System.IO.IsolatedStorage.IsolatedStorageFile> modułu wyliczającego.</span><span class="sxs-lookup"><span data-stu-id="9bc8e-104">This  method takes an <xref:System.IO.IsolatedStorage.IsolatedStorageScope> value and returns an <xref:System.IO.IsolatedStorage.IsolatedStorageFile> enumerator.</span></span> <span data-ttu-id="9bc8e-105">Aby wyliczyć magazynów, musisz mieć <xref:System.Security.Permissions.IsolatedStorageFilePermission> uprawnień, który określa <xref:System.Security.Permissions.IsolatedStorageContainment.AdministerIsolatedStorageByUser> wartość.</span><span class="sxs-lookup"><span data-stu-id="9bc8e-105">To enumerate stores, you must have the <xref:System.Security.Permissions.IsolatedStorageFilePermission> permission that specifies the <xref:System.Security.Permissions.IsolatedStorageContainment.AdministerIsolatedStorageByUser> value.</span></span> <span data-ttu-id="9bc8e-106">Jeśli należy wywołać <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetEnumerator%2A> metody z <xref:System.IO.IsolatedStorage.IsolatedStorageScope.User> wartości, zwraca tablicę <xref:System.IO.IsolatedStorage.IsolatedStorageFile> obiektów, które są zdefiniowane dla bieżącego użytkownika.</span><span class="sxs-lookup"><span data-stu-id="9bc8e-106">If you call the <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetEnumerator%2A> method with the <xref:System.IO.IsolatedStorage.IsolatedStorageScope.User> value, it returns an array of <xref:System.IO.IsolatedStorage.IsolatedStorageFile> objects that are defined for the current user.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9bc8e-107">Przykład</span><span class="sxs-lookup"><span data-stu-id="9bc8e-107">Example</span></span>  
 <span data-ttu-id="9bc8e-108">Poniższy przykładowy kod uzyskuje sklepu, która jest izolowana przez użytkownika i zestawu, tworzy kilka plików i pobiera pliki przy użyciu <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetEnumerator%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="9bc8e-108">The following code example obtains a store that is isolated by user and assembly, creates a few files, and retrieves those files by using the <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetEnumerator%2A> method.</span></span>  
  
 [!code-csharp[Conceptual.IsolatedStorage#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source2.cs#2)]
 [!code-vb[Conceptual.IsolatedStorage#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source2.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="9bc8e-109">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="9bc8e-109">See Also</span></span>  
 <xref:System.IO.IsolatedStorage.IsolatedStorageFile>  
 [<span data-ttu-id="9bc8e-110">Wydzielona pamięć masowa</span><span class="sxs-lookup"><span data-stu-id="9bc8e-110">Isolated Storage</span></span>](../../../docs/standard/io/isolated-storage.md)
