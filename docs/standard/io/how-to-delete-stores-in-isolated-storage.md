---
title: 'Porady: usuwanie danych z izolowanego magazynu'
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
- stores, deleting
- data stores, deleting
- deleting stores
- removing stores
- isolated storage, deleting stores
- storing data using isolated storage, deleting stores
- data storage using isolated storage, deleting stores
ms.assetid: 3947e333-5af6-4601-b2f1-24d4d6129cf3
caps.latest.revision: "14"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 138d1688f22cdc3bfa542af5433b6dbf8139e840
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-delete-stores-in-isolated-storage"></a><span data-ttu-id="74a3d-102">Porady: usuwanie danych z izolowanego magazynu</span><span class="sxs-lookup"><span data-stu-id="74a3d-102">How to: Delete Stores in Isolated Storage</span></span>
<span data-ttu-id="74a3d-103"><xref:System.IO.IsolatedStorage.IsolatedStorageFile> Klasa zapewnia dwie metody usuwania plików izolowanych magazynów:</span><span class="sxs-lookup"><span data-stu-id="74a3d-103">The <xref:System.IO.IsolatedStorage.IsolatedStorageFile> class supplies two methods for deleting isolated storage files:</span></span>  
  
-   <span data-ttu-id="74a3d-104">Metoda wystąpienia <xref:System.IO.IsolatedStorage.IsolatedStorageFile.Remove> nie przyjmuje żadnych argumentów i usuwa magazynu, który wywołuje go.</span><span class="sxs-lookup"><span data-stu-id="74a3d-104">The instance method <xref:System.IO.IsolatedStorage.IsolatedStorageFile.Remove> does not take any arguments and deletes the store that calls it.</span></span> <span data-ttu-id="74a3d-105">Nie uprawnienia są wymagane do wykonania tej operacji.</span><span class="sxs-lookup"><span data-stu-id="74a3d-105">No permissions are required for this operation.</span></span> <span data-ttu-id="74a3d-106">Wszelki kod, który można uzyskać dostępu do magazynu można usunąć jednego lub wszystkich danych w nim.</span><span class="sxs-lookup"><span data-stu-id="74a3d-106">Any code that can access the store can delete any or all the data inside it.</span></span>  
  
-   <span data-ttu-id="74a3d-107">Statyczna metoda <xref:System.IO.IsolatedStorage.IsolatedStorageFile.Remove%28System.IO.IsolatedStorage.IsolatedStorageScope%29> przyjmuje <xref:System.IO.IsolatedStorage.IsolatedStorageScope.User> wartość wyliczenia i usuwa wszystkie sklepy dla użytkownika, który jest uruchomiony kod.</span><span class="sxs-lookup"><span data-stu-id="74a3d-107">The static method <xref:System.IO.IsolatedStorage.IsolatedStorageFile.Remove%28System.IO.IsolatedStorage.IsolatedStorageScope%29> takes the <xref:System.IO.IsolatedStorage.IsolatedStorageScope.User> enumeration value, and deletes all the stores for the user who is running the code.</span></span> <span data-ttu-id="74a3d-108">Ta operacja wymaga <xref:System.Security.Permissions.IsolatedStorageFilePermission> uprawnienie <xref:System.Security.Permissions.IsolatedStorageContainment.AdministerIsolatedStorageByUser> wartość.</span><span class="sxs-lookup"><span data-stu-id="74a3d-108">This operation requires <xref:System.Security.Permissions.IsolatedStorageFilePermission> permission for the <xref:System.Security.Permissions.IsolatedStorageContainment.AdministerIsolatedStorageByUser> value.</span></span>  
  
## <a name="example"></a><span data-ttu-id="74a3d-109">Przykład</span><span class="sxs-lookup"><span data-stu-id="74a3d-109">Example</span></span>  
 <span data-ttu-id="74a3d-110">Poniższy przykład kodu pokazuje używania statycznych i wystąpienia <xref:System.IO.IsolatedStorage.IsolatedStorageFile.Remove%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="74a3d-110">The following code example demonstrates the use of the static and instance <xref:System.IO.IsolatedStorage.IsolatedStorageFile.Remove%2A> methods.</span></span> <span data-ttu-id="74a3d-111">Klasy pobiera dwa magazynów; jedna jest izolowane dla użytkownika i zestawu, a drugi to izolowane dla użytkownika, domena i zestawu.</span><span class="sxs-lookup"><span data-stu-id="74a3d-111">The class obtains two stores; one is isolated for user and assembly and the other is isolated for user, domain, and assembly.</span></span> <span data-ttu-id="74a3d-112">Magazynie użytkownika, domena i zestawu jest usuwany przez wywołanie metody <xref:System.IO.IsolatedStorage.IsolatedStorageFile.Remove> metody w pliku izolowanego magazynu `isoStore1`.</span><span class="sxs-lookup"><span data-stu-id="74a3d-112">The user, domain, and assembly store is then deleted by calling the <xref:System.IO.IsolatedStorage.IsolatedStorageFile.Remove> method of the isolated storage file  `isoStore1`.</span></span> <span data-ttu-id="74a3d-113">Następnie wszystkie pozostałe magazynów dla użytkownika zostaną usunięte przez wywołanie metody statycznej <xref:System.IO.IsolatedStorage.IsolatedStorageFile.Remove%28System.IO.IsolatedStorage.IsolatedStorageScope%29>.</span><span class="sxs-lookup"><span data-stu-id="74a3d-113">Then, all remaining stores for the user are deleted by calling the static method <xref:System.IO.IsolatedStorage.IsolatedStorageFile.Remove%28System.IO.IsolatedStorage.IsolatedStorageScope%29>.</span></span>  
  
 [!code-cpp[Conceptual.IsolatedStorage#3](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source3.cpp#3)]
 [!code-csharp[Conceptual.IsolatedStorage#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source3.cs#3)]
 [!code-vb[Conceptual.IsolatedStorage#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source3.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="74a3d-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="74a3d-114">See Also</span></span>  
 <xref:System.IO.IsolatedStorage.IsolatedStorageFile>  
 [<span data-ttu-id="74a3d-115">Izolowany Magazyn</span><span class="sxs-lookup"><span data-stu-id="74a3d-115">Isolated Storage</span></span>](../../../docs/standard/io/isolated-storage.md)
