---
title: 'Porady: Tworzenie wstępnie obliczonych zadań'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- tasks, creating pre-computed
ms.assetid: a73eafa2-1f49-4106-a19e-997186029b58
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 47e4c5d721b37388a4008d100f5212057477c638
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2018
ms.locfileid: "44047925"
---
# <a name="how-to-create-pre-computed-tasks"></a><span data-ttu-id="413e6-102">Porady: Tworzenie wstępnie obliczonych zadań</span><span class="sxs-lookup"><span data-stu-id="413e6-102">How to: Create Pre-Computed Tasks</span></span>
<span data-ttu-id="413e6-103">W tym dokumencie opisano, jak używać <xref:System.Threading.Tasks.Task.FromResult%2A?displayProperty=nameWithType> metody do pobierania wyników asynchronicznych operacji pobrania, które są przechowywane w pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="413e6-103">This document describes how to use the <xref:System.Threading.Tasks.Task.FromResult%2A?displayProperty=nameWithType> method to retrieve the results of asynchronous download operations that are held in a cache.</span></span> <span data-ttu-id="413e6-104"><xref:System.Threading.Tasks.Task.FromResult%2A> Metoda zwraca Zakończono <xref:System.Threading.Tasks.Task%601> obiekt, który przechowuje, podana jest wartość jako jego <xref:System.Threading.Tasks.Task%601.Result%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="413e6-104">The <xref:System.Threading.Tasks.Task.FromResult%2A> method returns a finished <xref:System.Threading.Tasks.Task%601> object that holds the provided value as its <xref:System.Threading.Tasks.Task%601.Result%2A> property.</span></span> <span data-ttu-id="413e6-105">Ta metoda jest przydatna, gdy wykonujesz operację asynchroniczną, która zwraca <xref:System.Threading.Tasks.Task%601> obiektu, a wynik tego obiektu <xref:System.Threading.Tasks.Task%601> obiektu jest już obliczony.</span><span class="sxs-lookup"><span data-stu-id="413e6-105">This method is useful when you perform an asynchronous operation that returns a <xref:System.Threading.Tasks.Task%601> object, and the result of that <xref:System.Threading.Tasks.Task%601> object is already computed.</span></span>  
  
## <a name="example"></a><span data-ttu-id="413e6-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="413e6-106">Example</span></span>  
 <span data-ttu-id="413e6-107">Poniższy przykład pobiera ciągi z sieci web.</span><span class="sxs-lookup"><span data-stu-id="413e6-107">The following example downloads strings from the web.</span></span> <span data-ttu-id="413e6-108">Definiuje `DownloadStringAsync` metody.</span><span class="sxs-lookup"><span data-stu-id="413e6-108">It defines the `DownloadStringAsync` method.</span></span> <span data-ttu-id="413e6-109">Ta metoda asynchronicznie pobiera ciągi z sieci web.</span><span class="sxs-lookup"><span data-stu-id="413e6-109">This method downloads strings from the web asynchronously.</span></span> <span data-ttu-id="413e6-110">W tym przykładzie również użyto <xref:System.Collections.Concurrent.ConcurrentDictionary%602> obiektu w pamięci podręcznej wyników poprzedniej operacji.</span><span class="sxs-lookup"><span data-stu-id="413e6-110">This example also uses a <xref:System.Collections.Concurrent.ConcurrentDictionary%602> object to cache the results of previous operations.</span></span> <span data-ttu-id="413e6-111">Jeśli adres wejściowe są przechowywane w tej pamięci podręcznej `DownloadStringAsync` używa <xref:System.Threading.Tasks.Task.FromResult%2A> metody do tworzenia <xref:System.Threading.Tasks.Task%601> obiekt, który przechowuje zawartość pod tym adresem.</span><span class="sxs-lookup"><span data-stu-id="413e6-111">If the input address is held in this cache, `DownloadStringAsync` uses the <xref:System.Threading.Tasks.Task.FromResult%2A> method to produce a <xref:System.Threading.Tasks.Task%601> object that holds the content at that address.</span></span> <span data-ttu-id="413e6-112">W przeciwnym razie `DownloadStringAsync` pobiera plik z sieci web i dodaje wynik do pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="413e6-112">Otherwise, `DownloadStringAsync` downloads the file from the web and adds the result to the cache.</span></span>  
  
 [!code-csharp[TPL_CachedDownloads#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_cacheddownloads/cs/cacheddownloads.cs#1)]
 [!code-vb[TPL_CachedDownloads#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_cacheddownloads/vb/cacheddownloads.vb#1)]  
  
 <span data-ttu-id="413e6-113">W tym przykładzie oblicza czas, który jest wymagany do pobierania wielu ciągów dwa razy.</span><span class="sxs-lookup"><span data-stu-id="413e6-113">This example computes the time that is required to download multiple strings two times.</span></span> <span data-ttu-id="413e6-114">Drugi zestaw operacji pobierania powinna trwać krócej niż pierwszy zestaw, ponieważ wyniki są przechowywane w pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="413e6-114">The second set of download operations should take less time than the first set because the results are held in the cache.</span></span> <span data-ttu-id="413e6-115"><xref:System.Threading.Tasks.Task.FromResult%2A> Metoda umożliwia `DownloadStringAsync` metodę w celu utworzenia <xref:System.Threading.Tasks.Task%601> obiektów, które zawierają te wstępnie obliczone wyniki.</span><span class="sxs-lookup"><span data-stu-id="413e6-115">The <xref:System.Threading.Tasks.Task.FromResult%2A> method enables the `DownloadStringAsync` method to create <xref:System.Threading.Tasks.Task%601> objects that hold these pre-computed results.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="413e6-116">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="413e6-116">Compiling the Code</span></span>  
 <span data-ttu-id="413e6-117">Kopiuj przykładowy kod i wklej go w projekcie programu Visual Studio lub wklej go w pliku o nazwie `CachedDownloads.cs` (`CachedDownloads.vb` dla języka Visual Basic), a następnie uruchom następujące polecenie w oknie wiersza polecenia programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="413e6-117">Copy the example code and paste it in a Visual Studio project, or paste it in a file that is named `CachedDownloads.cs` (`CachedDownloads.vb` for Visual Basic), and then run the following command in a Visual Studio Command Prompt window.</span></span>  
  
 <span data-ttu-id="413e6-118">Visual C#</span><span class="sxs-lookup"><span data-stu-id="413e6-118">Visual C#</span></span>  
  
 <span data-ttu-id="413e6-119">**CSC.exe CachedDownloads.cs**</span><span class="sxs-lookup"><span data-stu-id="413e6-119">**csc.exe CachedDownloads.cs**</span></span>  
  
 <span data-ttu-id="413e6-120">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="413e6-120">Visual Basic</span></span>  
  
 <span data-ttu-id="413e6-121">**vbc.exe CachedDownloads.vb**</span><span class="sxs-lookup"><span data-stu-id="413e6-121">**vbc.exe CachedDownloads.vb**</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="413e6-122">Niezawodne programowanie</span><span class="sxs-lookup"><span data-stu-id="413e6-122">Robust Programming</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="413e6-123">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="413e6-123">See also</span></span>

- [<span data-ttu-id="413e6-124">Programowanie asynchroniczne oparte na zadaniach</span><span class="sxs-lookup"><span data-stu-id="413e6-124">Task-based Asynchronous Programming</span></span>](../../../docs/standard/parallel-programming/task-based-asynchronous-programming.md)
