---
title: "Porady: Tworzenie wstępnie obliczonych zadań"
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
- tasks, creating pre-computed
ms.assetid: a73eafa2-1f49-4106-a19e-997186029b58
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 262aa626e9e426da94de0d2ad5f2ef04a5bbc5f3
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/23/2017
---
# <a name="how-to-create-pre-computed-tasks"></a><span data-ttu-id="30819-102">Porady: Tworzenie wstępnie obliczonych zadań</span><span class="sxs-lookup"><span data-stu-id="30819-102">How to: Create Pre-Computed Tasks</span></span>
<span data-ttu-id="30819-103">W tym dokumencie opisano sposób użycia <xref:System.Threading.Tasks.Task.FromResult%2A?displayProperty=nameWithType> metoda pobierania wyników operacji pobierania asynchroniczne, które są przechowywane w pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="30819-103">This document describes how to use the <xref:System.Threading.Tasks.Task.FromResult%2A?displayProperty=nameWithType> method to retrieve the results of asynchronous download operations that are held in a cache.</span></span> <span data-ttu-id="30819-104"><xref:System.Threading.Tasks.Task.FromResult%2A> Metoda zwraca Zakończono <xref:System.Threading.Tasks.Task%601> obiekt przechowujący podanej wartości jako jego <xref:System.Threading.Tasks.Task%601.Result%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="30819-104">The <xref:System.Threading.Tasks.Task.FromResult%2A> method returns a finished <xref:System.Threading.Tasks.Task%601> object that holds the provided value as its <xref:System.Threading.Tasks.Task%601.Result%2A> property.</span></span> <span data-ttu-id="30819-105">Ta metoda jest przydatna, gdy wykonujesz operację asynchroniczną, która zwraca <xref:System.Threading.Tasks.Task%601> obiektu i wynik tego <xref:System.Threading.Tasks.Task%601> obiekt już jest obliczana.</span><span class="sxs-lookup"><span data-stu-id="30819-105">This method is useful when you perform an asynchronous operation that returns a <xref:System.Threading.Tasks.Task%601> object, and the result of that <xref:System.Threading.Tasks.Task%601> object is already computed.</span></span>  
  
## <a name="example"></a><span data-ttu-id="30819-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="30819-106">Example</span></span>  
 <span data-ttu-id="30819-107">Poniższy przykład pobieranie ciągów z sieci web.</span><span class="sxs-lookup"><span data-stu-id="30819-107">The following example downloads strings from the web.</span></span> <span data-ttu-id="30819-108">Definiuje `DownloadStringAsync` metody.</span><span class="sxs-lookup"><span data-stu-id="30819-108">It defines the `DownloadStringAsync` method.</span></span> <span data-ttu-id="30819-109">Ta metoda pobiera asynchronicznie ciągów z sieci web.</span><span class="sxs-lookup"><span data-stu-id="30819-109">This method downloads strings from the web asynchronously.</span></span> <span data-ttu-id="30819-110">W tym przykładzie również używane <xref:System.Collections.Concurrent.ConcurrentDictionary%602> obiektu w pamięci podręcznej wyniki poprzedniej operacji.</span><span class="sxs-lookup"><span data-stu-id="30819-110">This example also uses a <xref:System.Collections.Concurrent.ConcurrentDictionary%602> object to cache the results of previous operations.</span></span> <span data-ttu-id="30819-111">Jeśli adres wejściowych odbywa się w tej pamięci podręcznej, `DownloadStringAsync` używa <xref:System.Threading.Tasks.Task.FromResult%2A> metodę, aby utworzyć <xref:System.Threading.Tasks.Task%601> obiektu z zawartością pod tym adresem.</span><span class="sxs-lookup"><span data-stu-id="30819-111">If the input address is held in this cache, `DownloadStringAsync` uses the <xref:System.Threading.Tasks.Task.FromResult%2A> method to produce a <xref:System.Threading.Tasks.Task%601> object that holds the content at that address.</span></span> <span data-ttu-id="30819-112">W przeciwnym razie `DownloadStringAsync` pobiera plik z sieci web i dodaje wynik do pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="30819-112">Otherwise, `DownloadStringAsync` downloads the file from the web and adds the result to the cache.</span></span>  
  
 [!code-csharp[TPL_CachedDownloads#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_cacheddownloads/cs/cacheddownloads.cs#1)]
 [!code-vb[TPL_CachedDownloads#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_cacheddownloads/vb/cacheddownloads.vb#1)]  
  
 <span data-ttu-id="30819-113">W tym przykładzie oblicza czas, który jest wymagany do pobrania wielu ciągów dwa razy.</span><span class="sxs-lookup"><span data-stu-id="30819-113">This example computes the time that is required to download multiple strings two times.</span></span> <span data-ttu-id="30819-114">Drugi zestaw operacji pobierania powinno zająć mniej czasu niż pierwszy zestaw, ponieważ wyniki są przechowywane w pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="30819-114">The second set of download operations should take less time than the first set because the results are held in the cache.</span></span> <span data-ttu-id="30819-115"><xref:System.Threading.Tasks.Task.FromResult%2A> Metody umożliwia `DownloadStringAsync` metodę w celu utworzenia <xref:System.Threading.Tasks.Task%601> obiektów, które zawierają te wstępnie obliczonych wyników.</span><span class="sxs-lookup"><span data-stu-id="30819-115">The <xref:System.Threading.Tasks.Task.FromResult%2A> method enables the `DownloadStringAsync` method to create <xref:System.Threading.Tasks.Task%601> objects that hold these pre-computed results.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="30819-116">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="30819-116">Compiling the Code</span></span>  
 <span data-ttu-id="30819-117">Skopiuj przykładowy kod i wklej go w projekcie programu Visual Studio lub wklej go w pliku o nazwie `CachedDownloads.cs` (`CachedDownloads.vb` dla [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]), a następnie uruchom następujące polecenie w oknie Wiersz polecenia programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="30819-117">Copy the example code and paste it in a Visual Studio project, or paste it in a file that is named `CachedDownloads.cs` (`CachedDownloads.vb` for [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]), and then run the following command in a Visual Studio Command Prompt window.</span></span>  
  
 [!INCLUDE[csprcs](../../../includes/csprcs-md.md)]  
  
 <span data-ttu-id="30819-118">**CSC.exe CachedDownloads.cs**</span><span class="sxs-lookup"><span data-stu-id="30819-118">**csc.exe CachedDownloads.cs**</span></span>  
  
 [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]  
  
 <span data-ttu-id="30819-119">**vbc.exe CachedDownloads.vb**</span><span class="sxs-lookup"><span data-stu-id="30819-119">**vbc.exe CachedDownloads.vb**</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="30819-120">Niezawodne programowanie</span><span class="sxs-lookup"><span data-stu-id="30819-120">Robust Programming</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="30819-121">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="30819-121">See Also</span></span>  
 [<span data-ttu-id="30819-122">Programowanie asynchroniczne oparte na zadaniach</span><span class="sxs-lookup"><span data-stu-id="30819-122">Task-based Asynchronous Programming</span></span>](../../../docs/standard/parallel-programming/task-based-asynchronous-programming.md)
