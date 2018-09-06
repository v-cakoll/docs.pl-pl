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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: cfb6111b080b7c8c359458e3fd1dc99cb0ff3c36
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2018
ms.locfileid: "43877323"
---
# <a name="how-to-delete-stores-in-isolated-storage"></a><span data-ttu-id="10a7c-102">Porady: usuwanie danych z izolowanego magazynu</span><span class="sxs-lookup"><span data-stu-id="10a7c-102">How to: Delete Stores in Isolated Storage</span></span>
<span data-ttu-id="10a7c-103"><xref:System.IO.IsolatedStorage.IsolatedStorageFile> Klasa zapewnia dwie metody usuwania plików wydzielonej pamięci masowej:</span><span class="sxs-lookup"><span data-stu-id="10a7c-103">The <xref:System.IO.IsolatedStorage.IsolatedStorageFile> class supplies two methods for deleting isolated storage files:</span></span>  
  
-   <span data-ttu-id="10a7c-104">Metoda wystąpienia <xref:System.IO.IsolatedStorage.IsolatedStorageFile.Remove> nie przyjmuje żadnych argumentów, a następnie usuwa magazynu, który ją wywołuje.</span><span class="sxs-lookup"><span data-stu-id="10a7c-104">The instance method <xref:System.IO.IsolatedStorage.IsolatedStorageFile.Remove> does not take any arguments and deletes the store that calls it.</span></span> <span data-ttu-id="10a7c-105">Nie uprawnienia są wymagane do wykonania tej operacji.</span><span class="sxs-lookup"><span data-stu-id="10a7c-105">No permissions are required for this operation.</span></span> <span data-ttu-id="10a7c-106">Wszelki kod, który można uzyskać dostępu do magazynu można usunąć dowolnych lub wszystkich danych wewnątrz niego.</span><span class="sxs-lookup"><span data-stu-id="10a7c-106">Any code that can access the store can delete any or all the data inside it.</span></span>  
  
-   <span data-ttu-id="10a7c-107">Metoda statyczna <xref:System.IO.IsolatedStorage.IsolatedStorageFile.Remove%28System.IO.IsolatedStorage.IsolatedStorageScope%29> przyjmuje <xref:System.IO.IsolatedStorage.IsolatedStorageScope.User> wartość wyliczenia i usuwa wszystkie magazyny dla użytkownika, który jest uruchomiony kod.</span><span class="sxs-lookup"><span data-stu-id="10a7c-107">The static method <xref:System.IO.IsolatedStorage.IsolatedStorageFile.Remove%28System.IO.IsolatedStorage.IsolatedStorageScope%29> takes the <xref:System.IO.IsolatedStorage.IsolatedStorageScope.User> enumeration value, and deletes all the stores for the user who is running the code.</span></span> <span data-ttu-id="10a7c-108">Ta operacja wymaga <xref:System.Security.Permissions.IsolatedStorageFilePermission> uprawnienia dla <xref:System.Security.Permissions.IsolatedStorageContainment.AdministerIsolatedStorageByUser> wartość.</span><span class="sxs-lookup"><span data-stu-id="10a7c-108">This operation requires <xref:System.Security.Permissions.IsolatedStorageFilePermission> permission for the <xref:System.Security.Permissions.IsolatedStorageContainment.AdministerIsolatedStorageByUser> value.</span></span>  
  
## <a name="example"></a><span data-ttu-id="10a7c-109">Przykład</span><span class="sxs-lookup"><span data-stu-id="10a7c-109">Example</span></span>  
 <span data-ttu-id="10a7c-110">Poniższy przykład kodu demonstruje użycie statycznych i wystąpienia <xref:System.IO.IsolatedStorage.IsolatedStorageFile.Remove%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="10a7c-110">The following code example demonstrates the use of the static and instance <xref:System.IO.IsolatedStorage.IsolatedStorageFile.Remove%2A> methods.</span></span> <span data-ttu-id="10a7c-111">Klasa uzyskuje dwóch magazynów; jeden jest izolowane dla użytkownika i zestawu, a drugi to izolowane i użytkownika, domeny i zestawu.</span><span class="sxs-lookup"><span data-stu-id="10a7c-111">The class obtains two stores; one is isolated for user and assembly and the other is isolated for user, domain, and assembly.</span></span> <span data-ttu-id="10a7c-112">Magazyn użytkownika, domeny i zestawu jest usuwany przez wywołanie metody <xref:System.IO.IsolatedStorage.IsolatedStorageFile.Remove> metoda pliku wydzielonej pamięci masowej `isoStore1`.</span><span class="sxs-lookup"><span data-stu-id="10a7c-112">The user, domain, and assembly store is then deleted by calling the <xref:System.IO.IsolatedStorage.IsolatedStorageFile.Remove> method of the isolated storage file  `isoStore1`.</span></span> <span data-ttu-id="10a7c-113">Następnie wszystkie pozostałe magazyny użytkownika są usuwane przez wywołanie metody statycznej <xref:System.IO.IsolatedStorage.IsolatedStorageFile.Remove%28System.IO.IsolatedStorage.IsolatedStorageScope%29>.</span><span class="sxs-lookup"><span data-stu-id="10a7c-113">Then, all remaining stores for the user are deleted by calling the static method <xref:System.IO.IsolatedStorage.IsolatedStorageFile.Remove%28System.IO.IsolatedStorage.IsolatedStorageScope%29>.</span></span>  
  
 [!code-cpp[Conceptual.IsolatedStorage#3](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source3.cpp#3)]
 [!code-csharp[Conceptual.IsolatedStorage#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source3.cs#3)]
 [!code-vb[Conceptual.IsolatedStorage#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source3.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="10a7c-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="10a7c-114">See also</span></span>

- <xref:System.IO.IsolatedStorage.IsolatedStorageFile>  
- [<span data-ttu-id="10a7c-115">Wydzielona pamięć masowa</span><span class="sxs-lookup"><span data-stu-id="10a7c-115">Isolated Storage</span></span>](../../../docs/standard/io/isolated-storage.md)
