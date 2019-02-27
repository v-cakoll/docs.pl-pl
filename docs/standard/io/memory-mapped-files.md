---
title: Pliki mapowane w pamięci
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- memory-mapped files
- inter-process communication
ms.assetid: a483d1b5-64aa-45b6-86ef-11b859f7f02e
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 6b4c1b075d54189d195ea38d421463ea6b9e6161
ms.sourcegitcommit: bd28ff1e312eaba9718c4f7ea272c2d4781a7cac
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/26/2019
ms.locfileid: "56835359"
---
# <a name="memory-mapped-files"></a><span data-ttu-id="54f56-102">Pliki mapowane w pamięci</span><span class="sxs-lookup"><span data-stu-id="54f56-102">Memory-Mapped Files</span></span>
<span data-ttu-id="54f56-103">Plik mapowany w pamięci zawiera zawartość pliku w pamięci wirtualnej.</span><span class="sxs-lookup"><span data-stu-id="54f56-103">A memory-mapped file contains the contents of a file in virtual memory.</span></span> <span data-ttu-id="54f56-104">To mapowanie między pliku i pamięci miejsca umożliwia aplikacji, w tym wiele procesów można modyfikować plik przez odczyt i zapis bezpośrednio do pamięci.</span><span class="sxs-lookup"><span data-stu-id="54f56-104">This mapping between a file and memory space enables an application, including multiple processes, to modify the file by reading and writing directly to the memory.</span></span> <span data-ttu-id="54f56-105">Począwszy od [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], można użyć kodu zarządzanego dostępu do zamapowanych w pamięci plików w taki sam sposób, że funkcji natywnych Windows dostęp do plików zamapowanych w pamięci, zgodnie z opisem w [pliki Managing Memory-Mapped](https://docs.microsoft.com/previous-versions/ms810613(v=msdn.10)).</span><span class="sxs-lookup"><span data-stu-id="54f56-105">Starting with the [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], you can use managed code to access memory-mapped files in the same way that native Windows functions access memory-mapped files, as described in [Managing Memory-Mapped Files](https://docs.microsoft.com/previous-versions/ms810613(v=msdn.10)).</span></span>  
  
 <span data-ttu-id="54f56-106">Istnieją dwa typy plików zamapowanych w pamięci:</span><span class="sxs-lookup"><span data-stu-id="54f56-106">There are two types of memory-mapped files:</span></span>  
  
-   <span data-ttu-id="54f56-107">Trwałe pliki mapowane w pamięci</span><span class="sxs-lookup"><span data-stu-id="54f56-107">Persisted memory-mapped files</span></span>  
  
     <span data-ttu-id="54f56-108">Trwałe pliki są pliki mapowane w pamięci, które są skojarzone z plikiem źródłowym, na dysku.</span><span class="sxs-lookup"><span data-stu-id="54f56-108">Persisted files are memory-mapped files that are associated with a source file on a disk.</span></span> <span data-ttu-id="54f56-109">Podczas ostatniego proces zakończył pracę z plikiem, dane są zapisywane do pliku źródłowego na dysku.</span><span class="sxs-lookup"><span data-stu-id="54f56-109">When the last process has finished working with the file, the data is saved to the source file on the disk.</span></span> <span data-ttu-id="54f56-110">Te pliki mapowane w pamięci są odpowiednie do pracy z plikami źródłowymi bardzo duże.</span><span class="sxs-lookup"><span data-stu-id="54f56-110">These memory-mapped files are suitable for working with extremely large source files.</span></span>  
  
-   <span data-ttu-id="54f56-111">Trwały inne niż pliki mapowane w pamięci</span><span class="sxs-lookup"><span data-stu-id="54f56-111">Non-persisted memory-mapped files</span></span>  
  
     <span data-ttu-id="54f56-112">Trwały inne niż pliki są pliki mapowane w pamięci, które nie są skojarzone z plikiem na dysku.</span><span class="sxs-lookup"><span data-stu-id="54f56-112">Non-persisted files are memory-mapped files that are not associated with a file on a disk.</span></span> <span data-ttu-id="54f56-113">Podczas ostatniego proces zakończył pracę z plikiem, dane zostaną utracone, a plik jest odzyskiwane przez wyrzucanie elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="54f56-113">When the last process has finished working with the file, the data is lost and the file is reclaimed by garbage collection.</span></span> <span data-ttu-id="54f56-114">Te pliki są odpowiednie do tworzenia współużytkowaną pamięć służącą do komunikacji międzyprocesowej (IPC).</span><span class="sxs-lookup"><span data-stu-id="54f56-114">These files are suitable for creating shared memory for inter-process communications (IPC).</span></span>  
  
## <a name="processes-views-and-managing-memory"></a><span data-ttu-id="54f56-115">Procesy, widoków i zarządzanie pamięci</span><span class="sxs-lookup"><span data-stu-id="54f56-115">Processes, Views, and Managing Memory</span></span>  
 <span data-ttu-id="54f56-116">Pliki mapowane w pamięci mogą być współużytkowane przez wiele procesów.</span><span class="sxs-lookup"><span data-stu-id="54f56-116">Memory-mapped files can be shared across multiple processes.</span></span> <span data-ttu-id="54f56-117">Procesy można mapować do tego samego pliku mapowanych na pamięć przy użyciu nazwą pospolitą, który jest przypisywany przez proces, która utworzyła plik.</span><span class="sxs-lookup"><span data-stu-id="54f56-117">Processes can map to the same memory-mapped file by using a common name that is assigned by the process that created the file.</span></span>  
  
 <span data-ttu-id="54f56-118">Aby pracować z plikiem mapowane w pamięci, należy utworzyć widok całego pliku mapowanych na pamięć lub jej część.</span><span class="sxs-lookup"><span data-stu-id="54f56-118">To work with a memory-mapped file, you must create a view of the entire memory-mapped file or a part of it.</span></span> <span data-ttu-id="54f56-119">Można również utworzyć wiele widoków, aby tę samą część plików zamapowanych w pamięci, tworząc w ten sposób pamięcią współbieżną.</span><span class="sxs-lookup"><span data-stu-id="54f56-119">You can also create multiple views to the same part of the memory-mapped file, thereby creating concurrent memory.</span></span> <span data-ttu-id="54f56-120">Dla dwóch widoków pozostaje współbieżnych muszą oni można tworzyć na podstawie tego samego pliku mapowanych na pamięć.</span><span class="sxs-lookup"><span data-stu-id="54f56-120">For two views to remain concurrent, they have to be created from the same memory-mapped file.</span></span>  
  
 <span data-ttu-id="54f56-121">Wiele widoków, może być również konieczne, jeśli plik jest większy niż rozmiar aplikacji logicznej pamięci miejsce dostępne na potrzeby mapowania (2 GB na komputerze 32-bitowy) pamięci.</span><span class="sxs-lookup"><span data-stu-id="54f56-121">Multiple views may also be necessary if the file is greater than the size of the application’s logical memory space available for memory mapping (2 GB on a 32-bit computer).</span></span>  
  
 <span data-ttu-id="54f56-122">Istnieją dwa typy widoków: przesyłanie strumieniowe dostępu do widoku oraz widoku swobodnego dostępu.</span><span class="sxs-lookup"><span data-stu-id="54f56-122">There are two types of views: stream access view and random access view.</span></span> <span data-ttu-id="54f56-123">Strumień dostępu do widoków na użytek dostępu sekwencyjnego do pliku; jest to zalecane w przypadku plików nietrwałe i IPC.</span><span class="sxs-lookup"><span data-stu-id="54f56-123">Use stream access views for sequential access to a file; this is recommended for non-persisted files and IPC.</span></span> <span data-ttu-id="54f56-124">Widoki swobodnego dostępu są preferowane w przypadku pracy z plikami utrwalonych.</span><span class="sxs-lookup"><span data-stu-id="54f56-124">Random access views are preferred for working with persisted files.</span></span>  
  
 <span data-ttu-id="54f56-125">Pliki mapowane w pamięci są dostępne za pośrednictwem Menedżera pamięci systemu operacyjnego, plik automatycznie zostanie poddana partycjonowaniu na liczbę stron i dostępne, zgodnie z potrzebami.</span><span class="sxs-lookup"><span data-stu-id="54f56-125">Memory-mapped files are accessed through the operating system’s memory manager, so the file is automatically partitioned into a number of pages and accessed as needed.</span></span> <span data-ttu-id="54f56-126">Nie masz do obsługi zarządzania pamięcią, samodzielnie.</span><span class="sxs-lookup"><span data-stu-id="54f56-126">You do not have to handle the memory management yourself.</span></span>  
  
 <span data-ttu-id="54f56-127">Na poniższej ilustracji przedstawiono sposób wielu procesów może mieć wiele i nakładających się widoki do tego samego pliku mapowane w pamięci, w tym samym czasie.</span><span class="sxs-lookup"><span data-stu-id="54f56-127">The following illustration shows how multiple processes can have multiple and overlapping views to the same memory-mapped file at the same time.</span></span>  
  
 <span data-ttu-id="54f56-128">![Zawiera widoki pamięci&#45;mapowane pliku. ](../../../docs/standard/io/media/memmappersisted.png "MemMapPersisted")</span><span class="sxs-lookup"><span data-stu-id="54f56-128">![Shows views to a memory&#45;mapped file.](../../../docs/standard/io/media/memmappersisted.png "MemMapPersisted")</span></span>  
<span data-ttu-id="54f56-129">Wiele i nakładających się widoków z plikiem mapowane w pamięci</span><span class="sxs-lookup"><span data-stu-id="54f56-129">Multiple and overlapped views to a memory-mapped file</span></span>  
  
## <a name="programming-with-memory-mapped-files"></a><span data-ttu-id="54f56-130">Programowanie za pomocą pliki mapowane w pamięci</span><span class="sxs-lookup"><span data-stu-id="54f56-130">Programming with Memory-Mapped Files</span></span>  
 <span data-ttu-id="54f56-131">W poniższej tabeli przedstawiono wskazówki dotyczące korzystania z obiektów plików zamapowanych w pamięci oraz ich elementów członkowskich.</span><span class="sxs-lookup"><span data-stu-id="54f56-131">The following table provides a guide for using memory-mapped file objects and their members.</span></span>  
  
|<span data-ttu-id="54f56-132">Zadanie</span><span class="sxs-lookup"><span data-stu-id="54f56-132">Task</span></span>|<span data-ttu-id="54f56-133">Metody lub właściwości do użycia</span><span class="sxs-lookup"><span data-stu-id="54f56-133">Methods or properties to use</span></span>|  
|----------|----------------------------------|  
|<span data-ttu-id="54f56-134">Aby uzyskać <xref:System.IO.MemoryMappedFiles.MemoryMappedFile> obiekt, który reprezentuje utrwalonego pliku mapowane w pamięci z pliku na dysku.</span><span class="sxs-lookup"><span data-stu-id="54f56-134">To obtain a <xref:System.IO.MemoryMappedFiles.MemoryMappedFile> object that represents a persisted memory-mapped file from a file on disk.</span></span>|<span data-ttu-id="54f56-135"><xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateFromFile%2A?displayProperty=nameWithType> Metoda.</span><span class="sxs-lookup"><span data-stu-id="54f56-135"><xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateFromFile%2A?displayProperty=nameWithType> method.</span></span>|  
|<span data-ttu-id="54f56-136">Aby uzyskać <xref:System.IO.MemoryMappedFiles.MemoryMappedFile> obiekt, który reprezentuje plik mapowanych na pamięć nietrwałe (nie skojarzonych z plikiem na dysku).</span><span class="sxs-lookup"><span data-stu-id="54f56-136">To obtain a <xref:System.IO.MemoryMappedFiles.MemoryMappedFile> object that represents a non-persisted memory-mapped file (not associated with a file on disk).</span></span>|<span data-ttu-id="54f56-137"><xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateNew%2A?displayProperty=nameWithType> Metoda.</span><span class="sxs-lookup"><span data-stu-id="54f56-137"><xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateNew%2A?displayProperty=nameWithType> method.</span></span><br /><br /> <span data-ttu-id="54f56-138">- lub -</span><span class="sxs-lookup"><span data-stu-id="54f56-138">- or -</span></span><br /><br /> <span data-ttu-id="54f56-139"><xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateOrOpen%2A?displayProperty=nameWithType> Metoda.</span><span class="sxs-lookup"><span data-stu-id="54f56-139"><xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateOrOpen%2A?displayProperty=nameWithType> method.</span></span>|  
|<span data-ttu-id="54f56-140">Aby uzyskać <xref:System.IO.MemoryMappedFiles.MemoryMappedFile> obiekt istniejący plik mapowane w pamięci (utrwalona lub nieutrwaloną).</span><span class="sxs-lookup"><span data-stu-id="54f56-140">To obtain a <xref:System.IO.MemoryMappedFiles.MemoryMappedFile> object of an existing memory-mapped file (either persisted or non-persisted).</span></span>|<span data-ttu-id="54f56-141"><xref:System.IO.MemoryMappedFiles.MemoryMappedFile.OpenExisting%2A?displayProperty=nameWithType> Metoda.</span><span class="sxs-lookup"><span data-stu-id="54f56-141"><xref:System.IO.MemoryMappedFiles.MemoryMappedFile.OpenExisting%2A?displayProperty=nameWithType> method.</span></span>|  
|<span data-ttu-id="54f56-142">Aby uzyskać <xref:System.IO.UnmanagedMemoryStream> obiektu w celu wyświetlenia sekwencyjnie używanych do plików mapowanych na pamięć.</span><span class="sxs-lookup"><span data-stu-id="54f56-142">To obtain a <xref:System.IO.UnmanagedMemoryStream> object for a sequentially accessed view to the memory-mapped file.</span></span>|<span data-ttu-id="54f56-143"><xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateViewStream%2A?displayProperty=nameWithType> Metoda.</span><span class="sxs-lookup"><span data-stu-id="54f56-143"><xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateViewStream%2A?displayProperty=nameWithType> method.</span></span>|  
|<span data-ttu-id="54f56-144">Aby uzyskać <xref:System.IO.UnmanagedMemoryAccessor> obiektu w celu wyświetlenia swobodnego dostępu do zamapowanych w pamięci plik.</span><span class="sxs-lookup"><span data-stu-id="54f56-144">To obtain a <xref:System.IO.UnmanagedMemoryAccessor> object for a random access view to a memory-mapped fie.</span></span>|<span data-ttu-id="54f56-145"><xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateViewAccessor%2A?displayProperty=nameWithType> Metoda.</span><span class="sxs-lookup"><span data-stu-id="54f56-145"><xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateViewAccessor%2A?displayProperty=nameWithType> method.</span></span>|  
|<span data-ttu-id="54f56-146">Aby uzyskać <xref:Microsoft.Win32.SafeHandles.SafeMemoryMappedViewHandle> obiekt ma być używany z kodem niezarządzanym.</span><span class="sxs-lookup"><span data-stu-id="54f56-146">To obtain a <xref:Microsoft.Win32.SafeHandles.SafeMemoryMappedViewHandle> object to use with unmanaged code.</span></span>|<span data-ttu-id="54f56-147"><xref:System.IO.MemoryMappedFiles.MemoryMappedFile.SafeMemoryMappedFileHandle%2A?displayProperty=nameWithType> Właściwość.</span><span class="sxs-lookup"><span data-stu-id="54f56-147"><xref:System.IO.MemoryMappedFiles.MemoryMappedFile.SafeMemoryMappedFileHandle%2A?displayProperty=nameWithType> property.</span></span><br /><br /> <span data-ttu-id="54f56-148">- lub -</span><span class="sxs-lookup"><span data-stu-id="54f56-148">- or -</span></span><br /><br /> <span data-ttu-id="54f56-149"><xref:System.IO.MemoryMappedFiles.MemoryMappedViewAccessor.SafeMemoryMappedViewHandle%2A?displayProperty=nameWithType> Właściwość.</span><span class="sxs-lookup"><span data-stu-id="54f56-149"><xref:System.IO.MemoryMappedFiles.MemoryMappedViewAccessor.SafeMemoryMappedViewHandle%2A?displayProperty=nameWithType> property.</span></span><br /><br /> <span data-ttu-id="54f56-150">- lub -</span><span class="sxs-lookup"><span data-stu-id="54f56-150">- or -</span></span><br /><br /> <span data-ttu-id="54f56-151"><xref:System.IO.MemoryMappedFiles.MemoryMappedViewStream.SafeMemoryMappedViewHandle%2A?displayProperty=nameWithType> Właściwość.</span><span class="sxs-lookup"><span data-stu-id="54f56-151"><xref:System.IO.MemoryMappedFiles.MemoryMappedViewStream.SafeMemoryMappedViewHandle%2A?displayProperty=nameWithType> property.</span></span>|  
|<span data-ttu-id="54f56-152">Opóźnienia alokacji pamięci, aż widok jest tworzony (tylko nieutrwaloną pliki).</span><span class="sxs-lookup"><span data-stu-id="54f56-152">To delay allocating memory until a view is created (non-persisted files only).</span></span><br /><br /> <span data-ttu-id="54f56-153">(Aby określić bieżący rozmiar strony systemowej, należy użyć <xref:System.Environment.SystemPageSize%2A?displayProperty=nameWithType> właściwości.)</span><span class="sxs-lookup"><span data-stu-id="54f56-153">(To determine the current system page size, use the <xref:System.Environment.SystemPageSize%2A?displayProperty=nameWithType> property.)</span></span>|<span data-ttu-id="54f56-154"><xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateNew%2A> Metoda o <xref:System.IO.MemoryMappedFiles.MemoryMappedFileOptions.DelayAllocatePages?displayProperty=nameWithType> wartość.</span><span class="sxs-lookup"><span data-stu-id="54f56-154"><xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateNew%2A> method with the <xref:System.IO.MemoryMappedFiles.MemoryMappedFileOptions.DelayAllocatePages?displayProperty=nameWithType> value.</span></span><br /><br /> <span data-ttu-id="54f56-155">- lub -</span><span class="sxs-lookup"><span data-stu-id="54f56-155">- or -</span></span><br /><br /> <span data-ttu-id="54f56-156"><xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateOrOpen%2A> metody, które mają <xref:System.IO.MemoryMappedFiles.MemoryMappedFileOptions> wyliczenia jako parametr.</span><span class="sxs-lookup"><span data-stu-id="54f56-156"><xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateOrOpen%2A> methods that have a <xref:System.IO.MemoryMappedFiles.MemoryMappedFileOptions> enumeration as a parameter.</span></span>|  
  
### <a name="security"></a><span data-ttu-id="54f56-157">Zabezpieczenia</span><span class="sxs-lookup"><span data-stu-id="54f56-157">Security</span></span>  
 <span data-ttu-id="54f56-158">Prawa dostępu można zastosować podczas tworzenia pliku mapowanych na pamięć przy użyciu następujących metod, które przyjmują <xref:System.IO.MemoryMappedFiles.MemoryMappedFileAccess> wyliczenia jako parametr:</span><span class="sxs-lookup"><span data-stu-id="54f56-158">You can apply access rights when you create a memory-mapped file, by using the following methods that take a <xref:System.IO.MemoryMappedFiles.MemoryMappedFileAccess> enumeration as a parameter:</span></span>  
  
-   <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateFromFile%2A?displayProperty=nameWithType>  
  
-   <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateNew%2A?displayProperty=nameWithType>  
  
-   <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateOrOpen%2A?displayProperty=nameWithType>  
  
 <span data-ttu-id="54f56-159">Można określić uprawnienia do otwierania istniejącego pliku mapowanych na pamięć przy użyciu <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.OpenExisting%2A> metod, które przyjmują <xref:System.IO.MemoryMappedFiles.MemoryMappedFileRights> jako parametr.</span><span class="sxs-lookup"><span data-stu-id="54f56-159">You can specify access rights for opening an existing memory-mapped file by using the <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.OpenExisting%2A> methods that take an <xref:System.IO.MemoryMappedFiles.MemoryMappedFileRights> as a parameter.</span></span>  
  
 <span data-ttu-id="54f56-160">Ponadto, możesz dołączyć <xref:System.IO.MemoryMappedFiles.MemoryMappedFileSecurity> obiekt, który zawiera reguły dostępu do wstępnie zdefiniowane.</span><span class="sxs-lookup"><span data-stu-id="54f56-160">In addition, you can include a <xref:System.IO.MemoryMappedFiles.MemoryMappedFileSecurity> object that contains predefined access rules.</span></span>  
  
 <span data-ttu-id="54f56-161">Aby zastosować reguły dostępu do nowych lub zmienionych plików zamapowanych w pamięci, należy użyć <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.SetAccessControl%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="54f56-161">To apply new or changed access rules to a memory-mapped file, use the <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.SetAccessControl%2A> method.</span></span> <span data-ttu-id="54f56-162">Aby pobrać dostępu lub inspekcji reguły z istniejącego pliku, użyj <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.GetAccessControl%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="54f56-162">To retrieve access or audit rules from an existing file, use the <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.GetAccessControl%2A> method.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="54f56-163">Przykłady</span><span class="sxs-lookup"><span data-stu-id="54f56-163">Examples</span></span>  
  
### <a name="persisted-memory-mapped-files"></a><span data-ttu-id="54f56-164">Trwałe pliki mapowane w pamięci</span><span class="sxs-lookup"><span data-stu-id="54f56-164">Persisted Memory-Mapped Files</span></span>  
 <span data-ttu-id="54f56-165"><xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateFromFile%2A> Metod tworzenia pliku mapowane w pamięci z istniejącego pliku na dysku.</span><span class="sxs-lookup"><span data-stu-id="54f56-165">The <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateFromFile%2A> methods create a memory-mapped file from an existing file on disk.</span></span>  
  
 <span data-ttu-id="54f56-166">Poniższy przykład tworzy widok część bardzo dużych plików zamapowanych w pamięci i manipuluje jego części.</span><span class="sxs-lookup"><span data-stu-id="54f56-166">The following example creates a memory-mapped view of a part of an extremely large file and manipulates a portion of it.</span></span>  
  
 [!code-csharp[MemoryMappedFiles.MemoryMappedFile.CreateFromFile#1](../../../samples/snippets/csharp/VS_Snippets_CLR/memorymappedfiles.memorymappedfile.createfromfile/cs/program.cs#1)]
 [!code-vb[MemoryMappedFiles.MemoryMappedFile.CreateFromFile#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/memorymappedfiles.memorymappedfile.createfromfile/vb/program.vb#1)]  
  
 <span data-ttu-id="54f56-167">W poniższym przykładzie otwierany tego samego pliku mapowanych na pamięć na inny proces.</span><span class="sxs-lookup"><span data-stu-id="54f56-167">The following example opens the same memory-mapped file for another process.</span></span>  
  
 [!code-csharp[MemoryMappedFiles.MemoryMappedFile.OpenExisting#1](../../../samples/snippets/csharp/VS_Snippets_CLR/memorymappedfiles.memorymappedfile.openexisting/cs/program.cs#1)]
 [!code-vb[MemoryMappedFiles.MemoryMappedFile.OpenExisting#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/memorymappedfiles.memorymappedfile.openexisting/vb/program.vb#1)]  
  
### <a name="non-persisted-memory-mapped-files"></a><span data-ttu-id="54f56-168">Nietrwałe pliki mapowane w pamięci</span><span class="sxs-lookup"><span data-stu-id="54f56-168">Non-Persisted Memory-Mapped Files</span></span>  
 <span data-ttu-id="54f56-169"><xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateNew%2A> i <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateOrOpen%2A> metody tworzenia plików mapowanych na pamięć, który nie jest zamapowany do istniejącego pliku na dysku.</span><span class="sxs-lookup"><span data-stu-id="54f56-169">The <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateNew%2A> and <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateOrOpen%2A> methods create a memory-mapped file that is not mapped to an existing file on disk.</span></span>  
  
 <span data-ttu-id="54f56-170">Poniższy przykład składa się z trzech osobnych procesach (aplikacje konsoli), wartościami logicznymi zapisu w pliku mapowanych na pamięć.</span><span class="sxs-lookup"><span data-stu-id="54f56-170">The following example consists of three separate processes (console applications) that write Boolean values to a memory-mapped file.</span></span> <span data-ttu-id="54f56-171">Występuje następującą sekwencję czynności:</span><span class="sxs-lookup"><span data-stu-id="54f56-171">The following sequence of actions occur:</span></span>  
  
1.  <span data-ttu-id="54f56-172">`Process A` Tworzy plik mapowany w pamięci i zapisuje wartość.</span><span class="sxs-lookup"><span data-stu-id="54f56-172">`Process A` creates the memory-mapped file and writes a value to it.</span></span>  
  
2.  <span data-ttu-id="54f56-173">`Process B` Otwiera plik mapowany w pamięci i zapisuje wartość.</span><span class="sxs-lookup"><span data-stu-id="54f56-173">`Process B` opens the memory-mapped file and writes a value to it.</span></span>  
  
3.  <span data-ttu-id="54f56-174">`Process C` Otwiera plik mapowany w pamięci i zapisuje wartość.</span><span class="sxs-lookup"><span data-stu-id="54f56-174">`Process C` opens the memory-mapped file and writes a value to it.</span></span>  
  
4.  <span data-ttu-id="54f56-175">`Process A` odczytuje i wyświetla wartości z pliku mapowanych na pamięć.</span><span class="sxs-lookup"><span data-stu-id="54f56-175">`Process A` reads and displays the values from the memory-mapped file.</span></span>  
  
5.  <span data-ttu-id="54f56-176">Po `Process A` zostało zakończone z plikiem mapowane w pamięci, plik jest natychmiast odzyskiwane przez wyrzucanie elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="54f56-176">After `Process A` is finished with the memory-mapped file, the file is immediately reclaimed by garbage collection.</span></span>  
  
 <span data-ttu-id="54f56-177">Aby uruchomić ten przykład, wykonaj następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="54f56-177">To run this example, do the following:</span></span>  
  
1.  <span data-ttu-id="54f56-178">Kompiluj aplikacje, a następnie otwórz trzy okna wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="54f56-178">Compile the applications and open three Command Prompt windows.</span></span>  
  
2.  <span data-ttu-id="54f56-179">W pierwszym oknie wiersza polecenia, uruchom `Process A`.</span><span class="sxs-lookup"><span data-stu-id="54f56-179">In the first Command Prompt window, run `Process A`.</span></span>  
  
3.  <span data-ttu-id="54f56-180">W drugim oknie wiersza polecenia, uruchom `Process B`.</span><span class="sxs-lookup"><span data-stu-id="54f56-180">In the second Command Prompt window, run `Process B`.</span></span>  
  
4.  <span data-ttu-id="54f56-181">Wróć do `Process A` i naciśnij klawisz ENTER.</span><span class="sxs-lookup"><span data-stu-id="54f56-181">Return to `Process A` and press ENTER.</span></span>  
  
5.  <span data-ttu-id="54f56-182">W trzecim okno wiersza polecenia, uruchom `Process C`.</span><span class="sxs-lookup"><span data-stu-id="54f56-182">In the third Command Prompt window, run `Process C`.</span></span>  
  
6.  <span data-ttu-id="54f56-183">Wróć do `Process A` i naciśnij klawisz ENTER.</span><span class="sxs-lookup"><span data-stu-id="54f56-183">Return to `Process A` and press ENTER.</span></span>  
  
 <span data-ttu-id="54f56-184">Dane wyjściowe `Process A` jest następująca:</span><span class="sxs-lookup"><span data-stu-id="54f56-184">The output of `Process A` is as follows:</span></span>  
  
```  
Start Process B and press ENTER to continue.  
Start Process C and press ENTER to continue.  
Process A says: True  
Process B says: False  
Process C says: True  
```  
  
 <span data-ttu-id="54f56-185">**Proces A**</span><span class="sxs-lookup"><span data-stu-id="54f56-185">**Process A**</span></span>  
  
 [!code-csharp[System.IO.MemoryMappedFiles_IPC_X#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.memorymappedfiles_ipc_x/cs/program.cs#1)]
 [!code-vb[System.IO.MemoryMappedFiles_IPC_X#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.memorymappedfiles_ipc_x/vb/program.vb#1)]  
  
 <span data-ttu-id="54f56-186">**Proces B**</span><span class="sxs-lookup"><span data-stu-id="54f56-186">**Process B**</span></span>  
  
 [!code-csharp[System.IO.MemoryMappedFiles_IPC_A#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.memorymappedfiles_ipc_a/cs/program.cs#1)]
 [!code-vb[System.IO.MemoryMappedFiles_IPC_A#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.memorymappedfiles_ipc_a/vb/program.vb#1)]  
  
 <span data-ttu-id="54f56-187">**Proces C**</span><span class="sxs-lookup"><span data-stu-id="54f56-187">**Process C**</span></span>  
  
 [!code-csharp[System.IO.MemoryMappedFiles_IPC_B#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.memorymappedfiles_ipc_b/cs/program.cs#1)]
 [!code-vb[System.IO.MemoryMappedFiles_IPC_B#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.memorymappedfiles_ipc_b/vb/program.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="54f56-188">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="54f56-188">See also</span></span>

- [<span data-ttu-id="54f56-189">We/Wy plików i strumieni</span><span class="sxs-lookup"><span data-stu-id="54f56-189">File and Stream I/O</span></span>](../../../docs/standard/io/index.md)
