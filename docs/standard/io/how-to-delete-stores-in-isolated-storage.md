---
title: 'Porady: usuwanie danych z izolowanego magazynu'
ms.date: 03/30/2017
ms.technology: dotnet-standard
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
ms.openlocfilehash: 6b1e8e651fd8e18c79dd629c154fb6c4d74243e3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "75707830"
---
# <a name="how-to-delete-stores-in-isolated-storage"></a><span data-ttu-id="825bb-102">Porady: usuwanie danych z izolowanego magazynu</span><span class="sxs-lookup"><span data-stu-id="825bb-102">How to: Delete Stores in Isolated Storage</span></span>
<span data-ttu-id="825bb-103">Klasa <xref:System.IO.IsolatedStorage.IsolatedStorageFile> dostarcza dwie metody usuwania izolowanych plików magazynu:</span><span class="sxs-lookup"><span data-stu-id="825bb-103">The <xref:System.IO.IsolatedStorage.IsolatedStorageFile> class supplies two methods for deleting isolated storage files:</span></span>  
  
- <span data-ttu-id="825bb-104">Metoda <xref:System.IO.IsolatedStorage.IsolatedStorageFile.Remove> instance nie bierze żadnych argumentów i usuwa magazyn, który wywołuje go.</span><span class="sxs-lookup"><span data-stu-id="825bb-104">The instance method <xref:System.IO.IsolatedStorage.IsolatedStorageFile.Remove> does not take any arguments and deletes the store that calls it.</span></span> <span data-ttu-id="825bb-105">Dla tej operacji nie są wymagane żadne uprawnienia.</span><span class="sxs-lookup"><span data-stu-id="825bb-105">No permissions are required for this operation.</span></span> <span data-ttu-id="825bb-106">Każdy kod, który może uzyskać dostęp do magazynu można usunąć wszystkie lub wszystkie dane wewnątrz niego.</span><span class="sxs-lookup"><span data-stu-id="825bb-106">Any code that can access the store can delete any or all the data inside it.</span></span>  
  
- <span data-ttu-id="825bb-107">Metoda <xref:System.IO.IsolatedStorage.IsolatedStorageFile.Remove%28System.IO.IsolatedStorage.IsolatedStorageScope%29> statyczna <xref:System.IO.IsolatedStorage.IsolatedStorageScope.User> pobiera wartość wyliczenia i usuwa wszystkie magazyny dla użytkownika, który jest uruchomiony kod.</span><span class="sxs-lookup"><span data-stu-id="825bb-107">The static method <xref:System.IO.IsolatedStorage.IsolatedStorageFile.Remove%28System.IO.IsolatedStorage.IsolatedStorageScope%29> takes the <xref:System.IO.IsolatedStorage.IsolatedStorageScope.User> enumeration value, and deletes all the stores for the user who is running the code.</span></span> <span data-ttu-id="825bb-108">Ta operacja <xref:System.Security.Permissions.IsolatedStorageFilePermission> wymaga <xref:System.Security.Permissions.IsolatedStorageContainment.AdministerIsolatedStorageByUser> uprawnień dla wartości.</span><span class="sxs-lookup"><span data-stu-id="825bb-108">This operation requires <xref:System.Security.Permissions.IsolatedStorageFilePermission> permission for the <xref:System.Security.Permissions.IsolatedStorageContainment.AdministerIsolatedStorageByUser> value.</span></span>  
  
## <a name="example"></a><span data-ttu-id="825bb-109">Przykład</span><span class="sxs-lookup"><span data-stu-id="825bb-109">Example</span></span>  
 <span data-ttu-id="825bb-110">Poniższy przykład kodu pokazuje użycie metod statycznych i wystąpienia. <xref:System.IO.IsolatedStorage.IsolatedStorageFile.Remove%2A></span><span class="sxs-lookup"><span data-stu-id="825bb-110">The following code example demonstrates the use of the static and instance <xref:System.IO.IsolatedStorage.IsolatedStorageFile.Remove%2A> methods.</span></span> <span data-ttu-id="825bb-111">Klasa uzyskuje dwa magazyny; jeden jest izolowany dla użytkownika i zestawu, a drugi jest izolowany dla użytkownika, domeny i zestawu.</span><span class="sxs-lookup"><span data-stu-id="825bb-111">The class obtains two stores; one is isolated for user and assembly and the other is isolated for user, domain, and assembly.</span></span> <span data-ttu-id="825bb-112">Użytkownik, domena i magazyn zestawów są <xref:System.IO.IsolatedStorage.IsolatedStorageFile.Remove> następnie usuwane przez `isoStore1`wywołanie metody izolowanego pliku magazynu .</span><span class="sxs-lookup"><span data-stu-id="825bb-112">The user, domain, and assembly store is then deleted by calling the <xref:System.IO.IsolatedStorage.IsolatedStorageFile.Remove> method of the isolated storage file  `isoStore1`.</span></span> <span data-ttu-id="825bb-113">Następnie wszystkie pozostałe magazyny dla użytkownika są <xref:System.IO.IsolatedStorage.IsolatedStorageFile.Remove%28System.IO.IsolatedStorage.IsolatedStorageScope%29>usuwane przez wywołanie metody statycznej .</span><span class="sxs-lookup"><span data-stu-id="825bb-113">Then, all remaining stores for the user are deleted by calling the static method <xref:System.IO.IsolatedStorage.IsolatedStorageFile.Remove%28System.IO.IsolatedStorage.IsolatedStorageScope%29>.</span></span>  
  
 [!code-cpp[Conceptual.IsolatedStorage#3](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source3.cpp#3)]
 [!code-csharp[Conceptual.IsolatedStorage#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source3.cs#3)]
 [!code-vb[Conceptual.IsolatedStorage#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source3.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="825bb-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="825bb-114">See also</span></span>

- <xref:System.IO.IsolatedStorage.IsolatedStorageFile>
- [<span data-ttu-id="825bb-115">Izolowany magazyn</span><span class="sxs-lookup"><span data-stu-id="825bb-115">Isolated Storage</span></span>](../../../docs/standard/io/isolated-storage.md)
