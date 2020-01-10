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
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75707830"
---
# <a name="how-to-delete-stores-in-isolated-storage"></a><span data-ttu-id="05fc4-102">Porady: usuwanie danych z izolowanego magazynu</span><span class="sxs-lookup"><span data-stu-id="05fc4-102">How to: Delete Stores in Isolated Storage</span></span>
<span data-ttu-id="05fc4-103">Klasa <xref:System.IO.IsolatedStorage.IsolatedStorageFile> udostępnia dwie metody usuwania izolowanych plików magazynu:</span><span class="sxs-lookup"><span data-stu-id="05fc4-103">The <xref:System.IO.IsolatedStorage.IsolatedStorageFile> class supplies two methods for deleting isolated storage files:</span></span>  
  
- <span data-ttu-id="05fc4-104">Metoda wystąpienia <xref:System.IO.IsolatedStorage.IsolatedStorageFile.Remove> nie przyjmuje żadnych argumentów i usuwa magazyn, który go wywołuje.</span><span class="sxs-lookup"><span data-stu-id="05fc4-104">The instance method <xref:System.IO.IsolatedStorage.IsolatedStorageFile.Remove> does not take any arguments and deletes the store that calls it.</span></span> <span data-ttu-id="05fc4-105">Dla tej operacji nie są wymagane żadne uprawnienia.</span><span class="sxs-lookup"><span data-stu-id="05fc4-105">No permissions are required for this operation.</span></span> <span data-ttu-id="05fc4-106">Każdy kod, który może uzyskać dostęp do sklepu, może usunąć wszystkie lub wszystkie znajdujące się w nim dane.</span><span class="sxs-lookup"><span data-stu-id="05fc4-106">Any code that can access the store can delete any or all the data inside it.</span></span>  
  
- <span data-ttu-id="05fc4-107">Metoda statyczna <xref:System.IO.IsolatedStorage.IsolatedStorageFile.Remove%28System.IO.IsolatedStorage.IsolatedStorageScope%29> Pobiera wartość wyliczenia <xref:System.IO.IsolatedStorage.IsolatedStorageScope.User> i usuwa wszystkie magazyny dla użytkownika, który uruchomił kod.</span><span class="sxs-lookup"><span data-stu-id="05fc4-107">The static method <xref:System.IO.IsolatedStorage.IsolatedStorageFile.Remove%28System.IO.IsolatedStorage.IsolatedStorageScope%29> takes the <xref:System.IO.IsolatedStorage.IsolatedStorageScope.User> enumeration value, and deletes all the stores for the user who is running the code.</span></span> <span data-ttu-id="05fc4-108">Ta operacja wymaga uprawnień <xref:System.Security.Permissions.IsolatedStorageFilePermission> do wartości <xref:System.Security.Permissions.IsolatedStorageContainment.AdministerIsolatedStorageByUser>.</span><span class="sxs-lookup"><span data-stu-id="05fc4-108">This operation requires <xref:System.Security.Permissions.IsolatedStorageFilePermission> permission for the <xref:System.Security.Permissions.IsolatedStorageContainment.AdministerIsolatedStorageByUser> value.</span></span>  
  
## <a name="example"></a><span data-ttu-id="05fc4-109">Przykład</span><span class="sxs-lookup"><span data-stu-id="05fc4-109">Example</span></span>  
 <span data-ttu-id="05fc4-110">Poniższy przykład kodu demonstruje użycie metod statycznych i <xref:System.IO.IsolatedStorage.IsolatedStorageFile.Remove%2A> wystąpień.</span><span class="sxs-lookup"><span data-stu-id="05fc4-110">The following code example demonstrates the use of the static and instance <xref:System.IO.IsolatedStorage.IsolatedStorageFile.Remove%2A> methods.</span></span> <span data-ttu-id="05fc4-111">Klasa uzyskuje dwa magazyny; jeden jest izolowany dla użytkownika i zestawu, a drugi jest izolowany dla użytkownika, domeny i zestawu.</span><span class="sxs-lookup"><span data-stu-id="05fc4-111">The class obtains two stores; one is isolated for user and assembly and the other is isolated for user, domain, and assembly.</span></span> <span data-ttu-id="05fc4-112">Użytkownik, domena i magazyn zestawów są następnie usuwane przez wywołanie metody <xref:System.IO.IsolatedStorage.IsolatedStorageFile.Remove> `isoStore1`pliku magazynu izolowanego.</span><span class="sxs-lookup"><span data-stu-id="05fc4-112">The user, domain, and assembly store is then deleted by calling the <xref:System.IO.IsolatedStorage.IsolatedStorageFile.Remove> method of the isolated storage file  `isoStore1`.</span></span> <span data-ttu-id="05fc4-113">Następnie wszystkie pozostałe magazyny dla użytkownika są usuwane przez wywołanie metody statycznej <xref:System.IO.IsolatedStorage.IsolatedStorageFile.Remove%28System.IO.IsolatedStorage.IsolatedStorageScope%29>.</span><span class="sxs-lookup"><span data-stu-id="05fc4-113">Then, all remaining stores for the user are deleted by calling the static method <xref:System.IO.IsolatedStorage.IsolatedStorageFile.Remove%28System.IO.IsolatedStorage.IsolatedStorageScope%29>.</span></span>  
  
 [!code-cpp[Conceptual.IsolatedStorage#3](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source3.cpp#3)]
 [!code-csharp[Conceptual.IsolatedStorage#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source3.cs#3)]
 [!code-vb[Conceptual.IsolatedStorage#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source3.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="05fc4-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="05fc4-114">See also</span></span>

- <xref:System.IO.IsolatedStorage.IsolatedStorageFile>
- [<span data-ttu-id="05fc4-115">Wydzielona pamięć masowa</span><span class="sxs-lookup"><span data-stu-id="05fc4-115">Isolated Storage</span></span>](../../../docs/standard/io/isolated-storage.md)
