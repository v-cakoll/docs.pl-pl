---
title: "Porady: uzyskiwanie magazynów dla izolowanego magazynu"
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
- stores, obtaining
- storing data using isolated storage, obtaining stores
- isolated storage, obtaining stores
- data stores, obtaining
- data storage using isolated storage, obtaining stores
ms.assetid: fcb6b178-d526-47c4-b029-e946f880f9db
caps.latest.revision: "19"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 61f183398c3f8c93ead965036e1edeb200dd8cb1
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/23/2017
---
# <a name="how-to-obtain-stores-for-isolated-storage"></a><span data-ttu-id="51c34-102">Porady: uzyskiwanie magazynów dla izolowanego magazynu</span><span class="sxs-lookup"><span data-stu-id="51c34-102">How to: Obtain Stores for Isolated Storage</span></span>
<span data-ttu-id="51c34-103">Izolowane store ujawnia wirtualnym systemie plików w ramach przedziału danych.</span><span class="sxs-lookup"><span data-stu-id="51c34-103">An isolated store exposes a virtual file system within a data compartment.</span></span> <span data-ttu-id="51c34-104"><xref:System.IO.IsolatedStorage.IsolatedStorageFile> Klasa zapewnia kilka metod do interakcji z magazynu izolowanego.</span><span class="sxs-lookup"><span data-stu-id="51c34-104">The <xref:System.IO.IsolatedStorage.IsolatedStorageFile> class supplies a number of methods for interacting with an isolated store.</span></span> <span data-ttu-id="51c34-105">Aby utworzyć i pobrać magazynów, <xref:System.IO.IsolatedStorage.IsolatedStorageFile> oferuje trzy metody statycznej:</span><span class="sxs-lookup"><span data-stu-id="51c34-105">To create and retrieve stores, <xref:System.IO.IsolatedStorage.IsolatedStorageFile> provides three static methods:</span></span>  
  
-   <span data-ttu-id="51c34-106"><xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForAssembly%2A>Zwraca magazynu, która jest odizolowana przez użytkownika i zestawu.</span><span class="sxs-lookup"><span data-stu-id="51c34-106"><xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForAssembly%2A> returns storage that is isolated by user and assembly.</span></span>  
  
-   <span data-ttu-id="51c34-107"><xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForDomain%2A>Zwraca magazynu, który jest izolowana domena i zestawu.</span><span class="sxs-lookup"><span data-stu-id="51c34-107"><xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForDomain%2A> returns storage that is isolated by domain and assembly.</span></span>  
  
     <span data-ttu-id="51c34-108">Obie metody pobrać sklepu, która należy do kodu, w którym są one nazywane.</span><span class="sxs-lookup"><span data-stu-id="51c34-108">Both methods retrieve a store that belongs to the code from which they are called.</span></span>  
  
-   <span data-ttu-id="51c34-109">Statyczna metoda <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> zwraca izolowanego magazynu, określonej przez przekazywanie kombinacją parametrów zakresu.</span><span class="sxs-lookup"><span data-stu-id="51c34-109">The static method <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> returns an isolated store that is specified by passing in a combination of scope parameters.</span></span>  
  
 <span data-ttu-id="51c34-110">Poniższy kod zwraca sklepu, która jest odizolowana przez użytkownika, zestawu i domeny.</span><span class="sxs-lookup"><span data-stu-id="51c34-110">The following code returns a store that is isolated by user, assembly, and domain.</span></span>  
  
 [!code-cpp[Conceptual.IsolatedStorage#6](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source6.cpp#6)]
 [!code-csharp[Conceptual.IsolatedStorage#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source6.cs#6)]
 [!code-vb[Conceptual.IsolatedStorage#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source6.vb#6)]  
  
 <span data-ttu-id="51c34-111">Można użyć <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> metodę, aby określić, że magazyn powinno mieć Roaming z profilu użytkownika mobilnego.</span><span class="sxs-lookup"><span data-stu-id="51c34-111">You can use the <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> method to specify that a store should roam with a roaming user profile.</span></span> <span data-ttu-id="51c34-112">Aby uzyskać więcej informacji na temat tej konfiguracji, zobacz [typy izolacji](../../../docs/standard/io/types-of-isolation.md).</span><span class="sxs-lookup"><span data-stu-id="51c34-112">For details on how to set this up, see [Types of Isolation](../../../docs/standard/io/types-of-isolation.md).</span></span>  
  
 <span data-ttu-id="51c34-113">Izolowanych magazynów uzyskana w ramach różnych zestawów są domyślnie w sklepach.</span><span class="sxs-lookup"><span data-stu-id="51c34-113">Isolated stores obtained from within different assemblies are, by default, different stores.</span></span> <span data-ttu-id="51c34-114">Są dostępne w magazynie różnych zestawów lub domen przez przekazywanie w dowód zestawów lub domen w parametrach <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="51c34-114">You can access the store of a different assembly or domain by passing in the assembly or domain evidence in the parameters of the <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> method.</span></span> <span data-ttu-id="51c34-115">Wymaga to uprawnień dostępu do izolowanego magazynu za tożsamość domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="51c34-115">This requires permission to access isolated storage by application domain identity.</span></span> <span data-ttu-id="51c34-116">Aby uzyskać więcej informacji, zobacz <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> przeciążenia metody.</span><span class="sxs-lookup"><span data-stu-id="51c34-116">For more information, see the <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> method overloads.</span></span>  
  
 <span data-ttu-id="51c34-117"><xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForAssembly%2A>, <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForDomain%2A>, I <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> metody zwracają <xref:System.IO.IsolatedStorage.IsolatedStorageFile> obiektu.</span><span class="sxs-lookup"><span data-stu-id="51c34-117">The <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForAssembly%2A>, <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForDomain%2A>, and <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> methods return an <xref:System.IO.IsolatedStorage.IsolatedStorageFile> object.</span></span> <span data-ttu-id="51c34-118">Aby określić, jakiego typu izolacji jest najbardziej odpowiednia w danej sytuacji, zobacz [typy izolacji](../../../docs/standard/io/types-of-isolation.md).</span><span class="sxs-lookup"><span data-stu-id="51c34-118">To help you decide which isolation type is most appropriate for your situation, see [Types of Isolation](../../../docs/standard/io/types-of-isolation.md).</span></span> <span data-ttu-id="51c34-119">Jeśli masz obiektu pliku izolowanego magazynu można użyć metod izolowanych magazynów Odczyt, zapis, tworzenie i usuwanie plików i katalogów.</span><span class="sxs-lookup"><span data-stu-id="51c34-119">When you have an isolated storage file object, you can use the isolated storage methods to read, write, create, and delete files and directories.</span></span>  
  
 <span data-ttu-id="51c34-120">Nie istnieje mechanizm uniemożliwiający kodu przekazywanie <xref:System.IO.IsolatedStorage.IsolatedStorageFile> obiekt do kodu, który nie ma wystarczające prawa dostępu do pobrania samego magazynu.</span><span class="sxs-lookup"><span data-stu-id="51c34-120">There is no mechanism that prevents code from passing an <xref:System.IO.IsolatedStorage.IsolatedStorageFile> object to code that does not have sufficient access to get the store itself.</span></span> <span data-ttu-id="51c34-121">Domeny i zestawu tożsamości i uprawnienia izolowanych magazynów są sprawdzane tylko wtedy, gdy odwołanie do <xref:System.IO.IsolatedStorage.IsolatedStorage> obiektu są uzyskiwane, zwykle w <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForAssembly%2A>, <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForDomain%2A>, lub <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="51c34-121">Domain and assembly identities and isolated storage permissions are checked only when a reference to an <xref:System.IO.IsolatedStorage.IsolatedStorage> object is obtained, typically in the <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForAssembly%2A>, <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForDomain%2A>, or <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> method.</span></span> <span data-ttu-id="51c34-122">Odwołania do ochrony <xref:System.IO.IsolatedStorage.IsolatedStorageFile> obiektów, w związku z tym obowiązkiem jest kod, który używa tych odwołań.</span><span class="sxs-lookup"><span data-stu-id="51c34-122">Protecting references to <xref:System.IO.IsolatedStorage.IsolatedStorageFile> objects is, therefore, the responsibility of the code that uses these references.</span></span>  
  
## <a name="example"></a><span data-ttu-id="51c34-123">Przykład</span><span class="sxs-lookup"><span data-stu-id="51c34-123">Example</span></span>  
 <span data-ttu-id="51c34-124">Poniższy kod zapewnia prosty przykład klasy uzyskiwania sklepu, która jest odizolowana przez użytkownika i zestawu.</span><span class="sxs-lookup"><span data-stu-id="51c34-124">The following code provides a simple example of a class obtaining a store that is isolated by user and assembly.</span></span> <span data-ttu-id="51c34-125">Można zmienić kod można pobrać ze sklepu, która jest odizolowana przez użytkownika, domena i zestawu przez dodanie <xref:System.IO.IsolatedStorage.IsolatedStorageScope.Domain?displayProperty=nameWithType> do argumentów który <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> przekazuje metody.</span><span class="sxs-lookup"><span data-stu-id="51c34-125">The code can be changed to retrieve a store that is isolated by user, domain, and assembly by adding <xref:System.IO.IsolatedStorage.IsolatedStorageScope.Domain?displayProperty=nameWithType> to the arguments that the <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> method passes.</span></span>  
  
 <span data-ttu-id="51c34-126">Po uruchomieniu kodu, możesz sprawdzić, czy magazyn został utworzony przez wpisanie **/list StoreAdm** w wierszu polecenia.</span><span class="sxs-lookup"><span data-stu-id="51c34-126">After you run the code, you can confirm that a store was created by typing **StoreAdm /LIST** at the command line.</span></span> <span data-ttu-id="51c34-127">Ta funkcja jest uruchamiana [narzędzie izolowanych magazynów (Storeadm.exe)](../../../docs/framework/tools/storeadm-exe-isolated-storage-tool.md) i zawiera wszystkie bieżące izolowane magazynów dla użytkownika.</span><span class="sxs-lookup"><span data-stu-id="51c34-127">This runs the [Isolated Storage tool (Storeadm.exe)](../../../docs/framework/tools/storeadm-exe-isolated-storage-tool.md) and lists all the current isolated stores for the user.</span></span>  
  
 [!code-cpp[Conceptual.IsolatedStorage#7](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source6.cpp#7)]
 [!code-csharp[Conceptual.IsolatedStorage#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source6.cs#7)]
 [!code-vb[Conceptual.IsolatedStorage#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source6.vb#7)]  
  
## <a name="see-also"></a><span data-ttu-id="51c34-128">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="51c34-128">See Also</span></span>  
 <xref:System.IO.IsolatedStorage.IsolatedStorageFile>  
 <xref:System.IO.IsolatedStorage.IsolatedStorageScope>  
 [<span data-ttu-id="51c34-129">Wydzielona pamięć masowa</span><span class="sxs-lookup"><span data-stu-id="51c34-129">Isolated Storage</span></span>](../../../docs/standard/io/isolated-storage.md)  
 [<span data-ttu-id="51c34-130">Typy izolacji</span><span class="sxs-lookup"><span data-stu-id="51c34-130">Types of Isolation</span></span>](../../../docs/standard/io/types-of-isolation.md)  
 [<span data-ttu-id="51c34-131">Zestawy w środowisku uruchomieniowym CLR</span><span class="sxs-lookup"><span data-stu-id="51c34-131">Assemblies in the Common Language Runtime</span></span>](../../../docs/framework/app-domains/assemblies-in-the-common-language-runtime.md)
