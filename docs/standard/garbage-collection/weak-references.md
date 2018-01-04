---
title: "Słabe odwołania"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- weak references, short
- weak references, using
- weak references, long
- garbage collection, weak references
ms.assetid: 6a600fe5-3af3-4c64-82da-10a0a8e2d79b
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 3ca1331cc45f437882d38adba241e2767821de36
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/23/2017
---
# <a name="weak-references"></a><span data-ttu-id="23044-102">Słabe odwołania</span><span class="sxs-lookup"><span data-stu-id="23044-102">Weak References</span></span>
<span data-ttu-id="23044-103">Moduł zbierający elementy bezużyteczne nie można zebrać obiektu używany przez aplikację, gdy kod aplikacji może osiągnąć tego obiektu.</span><span class="sxs-lookup"><span data-stu-id="23044-103">The garbage collector cannot collect an object in use by an application while the application's code can reach that object.</span></span> <span data-ttu-id="23044-104">Aplikacja jest nazywany ma silne odwołanie do obiektu.</span><span class="sxs-lookup"><span data-stu-id="23044-104">The application is said to have a strong reference to the object.</span></span>  
  
 <span data-ttu-id="23044-105">Słabe odwołanie zezwala na moduł garbage collector zbierać obiektu, umożliwiając aplikacji dostępu do tego obiektu.</span><span class="sxs-lookup"><span data-stu-id="23044-105">A weak reference permits the garbage collector to collect the object while still allowing the application to access the object.</span></span> <span data-ttu-id="23044-106">Słabe odwołanie jest prawidłowy tylko w nieokreślonej ilość czasu, aż obiekt są gromadzone, gdy nie występują żadne relacje silne.</span><span class="sxs-lookup"><span data-stu-id="23044-106">A weak reference is valid only during the indeterminate amount of time until the object is collected when no strong references exist.</span></span> <span data-ttu-id="23044-107">Gdy używasz słabe odwołanie silne odwołanie do obiektu, który uniemożliwia zbieranych nadal można korzystać z aplikacji.</span><span class="sxs-lookup"><span data-stu-id="23044-107">When you use a weak reference, the application can still obtain a strong reference to the object, which prevents it from being collected.</span></span> <span data-ttu-id="23044-108">Jednak zawsze istnieje ryzyko, że moduł zbierający elementy bezużyteczne rozpocznie się obiekt najpierw przed ustanowieniu silne odwołanie.</span><span class="sxs-lookup"><span data-stu-id="23044-108">However, there is always the risk that the garbage collector will get to the object first before a strong reference is reestablished.</span></span>  
  
 <span data-ttu-id="23044-109">Słabe odwołania są przydatne w przypadku obiektów, które używają dużej ilości pamięci, ale można utworzyć ponownie łatwo Jeśli odzyskane przez wyrzucanie elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="23044-109">Weak references are useful for objects that use a lot of memory, but can be recreated easily if they are reclaimed by garbage collection.</span></span>  
  
 <span data-ttu-id="23044-110">Załóżmy, że widok drzewa w aplikacji formularzy systemu Windows wyświetla złożonych hierarchiczna wybór opcji dla użytkownika.</span><span class="sxs-lookup"><span data-stu-id="23044-110">Suppose a tree view in a Windows Forms application displays a complex hierarchical choice of options to the user.</span></span> <span data-ttu-id="23044-111">W przypadku dużych danych utrzymywanie drzewa w pamięci jest nieefektywne, gdy użytkownik jest związany z innych obiektów w aplikacji.</span><span class="sxs-lookup"><span data-stu-id="23044-111">If the underlying data is large, keeping the tree in memory is inefficient when the user is involved with something else in the application.</span></span>  
  
 <span data-ttu-id="23044-112">Gdy użytkownik zmienia optymalizacji na inną część aplikacji, można użyć <xref:System.WeakReference> klasa do tworzenia słabe odwołanie do drzewa i zniszczyć wszystkie odwołania silne.</span><span class="sxs-lookup"><span data-stu-id="23044-112">When the user switches away to another part of the application, you can use the <xref:System.WeakReference> class to create a weak reference to the tree and destroy all strong references.</span></span> <span data-ttu-id="23044-113">Gdy użytkownik przełącza do drzewa, aplikacja próbuje uzyskać silne odwołanie do drzewa i w razie powodzenia pozwala uniknąć Rekonstruowanie drzewa.</span><span class="sxs-lookup"><span data-stu-id="23044-113">When the user switches back to the tree, the application attempts to obtain a strong reference to the tree and, if successful, avoids reconstructing the tree.</span></span>  
  
 <span data-ttu-id="23044-114">Aby ustanowić słabe odwołanie z obiektem, należy utworzyć <xref:System.WeakReference> mają być śledzone za pomocą wystąpienia obiektu.</span><span class="sxs-lookup"><span data-stu-id="23044-114">To establish a weak reference with an object, you create a <xref:System.WeakReference> using the instance of the object to be tracked.</span></span> <span data-ttu-id="23044-115">Następnie ustaw <xref:System.WeakReference.Target%2A> właściwości tego obiektu i zestawu oryginalnej odwołanie do obiektu `null`.</span><span class="sxs-lookup"><span data-stu-id="23044-115">You then set the <xref:System.WeakReference.Target%2A> property to that object and set the original reference to the object to `null`.</span></span> <span data-ttu-id="23044-116">Na przykład kod, zobacz <xref:System.WeakReference> w bibliotece klas.</span><span class="sxs-lookup"><span data-stu-id="23044-116">For a code example, see <xref:System.WeakReference> in the class library.</span></span>  
  
## <a name="short-and-long-weak-references"></a><span data-ttu-id="23044-117">Krótko- i długi słabe odwołania</span><span class="sxs-lookup"><span data-stu-id="23044-117">Short and Long Weak References</span></span>  
 <span data-ttu-id="23044-118">Można utworzyć krótkiej słabe odwołanie lub długo słabego odwołania:</span><span class="sxs-lookup"><span data-stu-id="23044-118">You can create a short weak reference or a long weak reference:</span></span>  
  
-   <span data-ttu-id="23044-119">krótki</span><span class="sxs-lookup"><span data-stu-id="23044-119">Short</span></span>  
  
     <span data-ttu-id="23044-120">Element docelowy krótkich słabe odwołanie staje się `null` gdy obiekt jest odzyskana przez wyrzucanie elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="23044-120">The target of a short weak reference becomes `null` when the object is reclaimed by garbage collection.</span></span> <span data-ttu-id="23044-121">Słabe odwołanie jest obiekt zarządzany i mogą ulec wyrzucanie elementów bezużytecznych, podobnie jak inne obiektu zarządzanego.</span><span class="sxs-lookup"><span data-stu-id="23044-121">The weak reference is itself a managed object, and is subject to garbage collection just like any other managed object.</span></span>  <span data-ttu-id="23044-122">Krótki słabe odwołanie jest domyślnego konstruktora dla <xref:System.WeakReference>.</span><span class="sxs-lookup"><span data-stu-id="23044-122">A short weak reference is the default constructor for <xref:System.WeakReference>.</span></span>  
  
-   <span data-ttu-id="23044-123">długa</span><span class="sxs-lookup"><span data-stu-id="23044-123">Long</span></span>  
  
     <span data-ttu-id="23044-124">Long słabe odwołanie jest zachowywane po obiektu <xref:System.Object.Finalize%2A> została wywołana metoda.</span><span class="sxs-lookup"><span data-stu-id="23044-124">A long weak reference is retained after the object's <xref:System.Object.Finalize%2A> method has been called.</span></span> <span data-ttu-id="23044-125">Dzięki temu obiekt do odtworzenia, ale stan obiektu pozostaje nieprzewidywalne.</span><span class="sxs-lookup"><span data-stu-id="23044-125">This allows the object to be recreated, but the state of the object remains unpredictable.</span></span> <span data-ttu-id="23044-126">Aby korzystać z odwołaniem długie, określ `true` w <xref:System.WeakReference> konstruktora.</span><span class="sxs-lookup"><span data-stu-id="23044-126">To use a long reference, specify `true` in the <xref:System.WeakReference> constructor.</span></span>  
  
     <span data-ttu-id="23044-127">Jeśli typ obiektu nie ma <xref:System.Object.Finalize%2A> stosuje funkcji krótkich słabe odwołanie metody, a słabe odwołanie jest prawidłowe tylko do momentu docelowej są zbierane, co może nastąpić w dowolnym momencie po finalizatora jest uruchomienie.</span><span class="sxs-lookup"><span data-stu-id="23044-127">If the object's type does not have a <xref:System.Object.Finalize%2A> method, the short weak reference functionality applies and the weak reference is valid only until the target is collected, which can occur anytime after the finalizer is run.</span></span>  
  
 <span data-ttu-id="23044-128">Aby ustanowić silne odwołanie i ponownie użyć obiektu, rzutowania <xref:System.WeakReference.Target%2A> właściwość <xref:System.WeakReference> do typu obiektu.</span><span class="sxs-lookup"><span data-stu-id="23044-128">To establish a strong reference and use the object again, cast the <xref:System.WeakReference.Target%2A> property of a <xref:System.WeakReference> to the type of the object.</span></span> <span data-ttu-id="23044-129">Jeśli <xref:System.WeakReference.Target%2A> zwraca `null`, obiekt był zebranych; w przeciwnym razie, można nadal używać obiektu, ponieważ aplikacja została ponownie nawiązana silne odwołanie do niej.</span><span class="sxs-lookup"><span data-stu-id="23044-129">If the <xref:System.WeakReference.Target%2A> property returns `null`, the object was collected; otherwise, you can continue to use the object because the application has regained a strong reference to it.</span></span>  
  
## <a name="guidelines-for-using-weak-references"></a><span data-ttu-id="23044-130">Wskazówki dotyczące używania słabe odwołania</span><span class="sxs-lookup"><span data-stu-id="23044-130">Guidelines for Using Weak References</span></span>  
 <span data-ttu-id="23044-131">Użyj długo słabe odwołania tylko wtedy, gdy jest to konieczne, ponieważ stan obiektu jest nieprzewidziany po zakończeniu.</span><span class="sxs-lookup"><span data-stu-id="23044-131">Use long weak references only when necessary as the state of the object is unpredictable after finalization.</span></span>  
  
 <span data-ttu-id="23044-132">Unikaj używania słabego odwołania do obiektów małych wskaźnik sam może być tak dużych lub większy.</span><span class="sxs-lookup"><span data-stu-id="23044-132">Avoid using weak references to small objects because the pointer itself may be as large or larger.</span></span>  
  
 <span data-ttu-id="23044-133">Unikaj używania słabe odwołania jako automatyczne rozwiązanie problemów z zarządzaniem pamięci.</span><span class="sxs-lookup"><span data-stu-id="23044-133">Avoid using weak references as an automatic solution to memory management problems.</span></span> <span data-ttu-id="23044-134">Zamiast tego Tworzenie skutecznych zasad buforowania obsługi obiektów aplikacji.</span><span class="sxs-lookup"><span data-stu-id="23044-134">Instead, develop an effective caching policy for handling your application's objects.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="23044-135">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="23044-135">See Also</span></span>  
 [<span data-ttu-id="23044-136">Odzyskiwanie pamięci</span><span class="sxs-lookup"><span data-stu-id="23044-136">Garbage Collection</span></span>](../../../docs/standard/garbage-collection/index.md)
