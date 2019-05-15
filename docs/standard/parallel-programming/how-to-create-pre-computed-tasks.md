---
title: 'Instrukcje: Tworzenie wstępnie obliczonych zadań'
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
ms.openlocfilehash: 5e68465b6fae39089600457414e7f2a2328f725b
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/14/2019
ms.locfileid: "65593123"
---
# <a name="how-to-create-pre-computed-tasks"></a><span data-ttu-id="47115-102">Instrukcje: Tworzenie wstępnie obliczonych zadań</span><span class="sxs-lookup"><span data-stu-id="47115-102">How to: Create Pre-Computed Tasks</span></span>
<span data-ttu-id="47115-103">W tym dokumencie opisano, jak używać <xref:System.Threading.Tasks.Task.FromResult%2A?displayProperty=nameWithType> metody do pobierania wyników asynchronicznych operacji pobrania, które są przechowywane w pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="47115-103">This document describes how to use the <xref:System.Threading.Tasks.Task.FromResult%2A?displayProperty=nameWithType> method to retrieve the results of asynchronous download operations that are held in a cache.</span></span> <span data-ttu-id="47115-104"><xref:System.Threading.Tasks.Task.FromResult%2A> Metoda zwraca Zakończono <xref:System.Threading.Tasks.Task%601> obiekt, który przechowuje, podana jest wartość jako jego <xref:System.Threading.Tasks.Task%601.Result%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="47115-104">The <xref:System.Threading.Tasks.Task.FromResult%2A> method returns a finished <xref:System.Threading.Tasks.Task%601> object that holds the provided value as its <xref:System.Threading.Tasks.Task%601.Result%2A> property.</span></span> <span data-ttu-id="47115-105">Ta metoda jest przydatna, gdy wykonujesz operację asynchroniczną, która zwraca <xref:System.Threading.Tasks.Task%601> obiektu, a wynik tego obiektu <xref:System.Threading.Tasks.Task%601> obiektu jest już obliczony.</span><span class="sxs-lookup"><span data-stu-id="47115-105">This method is useful when you perform an asynchronous operation that returns a <xref:System.Threading.Tasks.Task%601> object, and the result of that <xref:System.Threading.Tasks.Task%601> object is already computed.</span></span>  
  
## <a name="example"></a><span data-ttu-id="47115-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="47115-106">Example</span></span>  
 <span data-ttu-id="47115-107">Poniższy przykład pobiera ciągi z sieci web.</span><span class="sxs-lookup"><span data-stu-id="47115-107">The following example downloads strings from the web.</span></span> <span data-ttu-id="47115-108">Definiuje `DownloadStringAsync` metody.</span><span class="sxs-lookup"><span data-stu-id="47115-108">It defines the `DownloadStringAsync` method.</span></span> <span data-ttu-id="47115-109">Ta metoda asynchronicznie pobiera ciągi z sieci web.</span><span class="sxs-lookup"><span data-stu-id="47115-109">This method downloads strings from the web asynchronously.</span></span> <span data-ttu-id="47115-110">W tym przykładzie również użyto <xref:System.Collections.Concurrent.ConcurrentDictionary%602> obiektu w pamięci podręcznej wyników poprzedniej operacji.</span><span class="sxs-lookup"><span data-stu-id="47115-110">This example also uses a <xref:System.Collections.Concurrent.ConcurrentDictionary%602> object to cache the results of previous operations.</span></span> <span data-ttu-id="47115-111">Jeśli adres wejściowe są przechowywane w tej pamięci podręcznej `DownloadStringAsync` używa <xref:System.Threading.Tasks.Task.FromResult%2A> metody do tworzenia <xref:System.Threading.Tasks.Task%601> obiekt, który przechowuje zawartość pod tym adresem.</span><span class="sxs-lookup"><span data-stu-id="47115-111">If the input address is held in this cache, `DownloadStringAsync` uses the <xref:System.Threading.Tasks.Task.FromResult%2A> method to produce a <xref:System.Threading.Tasks.Task%601> object that holds the content at that address.</span></span> <span data-ttu-id="47115-112">W przeciwnym razie `DownloadStringAsync` pobiera plik z sieci web i dodaje wynik do pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="47115-112">Otherwise, `DownloadStringAsync` downloads the file from the web and adds the result to the cache.</span></span>  
  
 [!code-csharp[TPL_CachedDownloads#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_cacheddownloads/cs/cacheddownloads.cs#1)]
 [!code-vb[TPL_CachedDownloads#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_cacheddownloads/vb/cacheddownloads.vb#1)]  
  
 <span data-ttu-id="47115-113">W tym przykładzie oblicza czas, który jest wymagany do pobierania wielu ciągów dwa razy.</span><span class="sxs-lookup"><span data-stu-id="47115-113">This example computes the time that is required to download multiple strings two times.</span></span> <span data-ttu-id="47115-114">Drugi zestaw operacji pobierania powinna trwać krócej niż pierwszy zestaw, ponieważ wyniki są przechowywane w pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="47115-114">The second set of download operations should take less time than the first set because the results are held in the cache.</span></span> <span data-ttu-id="47115-115"><xref:System.Threading.Tasks.Task.FromResult%2A> Metoda umożliwia `DownloadStringAsync` metodę w celu utworzenia <xref:System.Threading.Tasks.Task%601> obiektów, które zawierają te wstępnie obliczone wyniki.</span><span class="sxs-lookup"><span data-stu-id="47115-115">The <xref:System.Threading.Tasks.Task.FromResult%2A> method enables the `DownloadStringAsync` method to create <xref:System.Threading.Tasks.Task%601> objects that hold these pre-computed results.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="47115-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="47115-116">See also</span></span>

- [<span data-ttu-id="47115-117">Programowanie asynchroniczne oparte na zadaniach</span><span class="sxs-lookup"><span data-stu-id="47115-117">Task-based Asynchronous Programming</span></span>](../../../docs/standard/parallel-programming/task-based-asynchronous-programming.md)
