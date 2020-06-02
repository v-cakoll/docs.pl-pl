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
ms.openlocfilehash: 88f0782380d21858bc5dd0fc0fbf63bbf85403b8
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2020
ms.locfileid: "84289996"
---
# <a name="how-to-create-pre-computed-tasks"></a><span data-ttu-id="55c42-102">Instrukcje: Tworzenie wstępnie obliczonych zadań</span><span class="sxs-lookup"><span data-stu-id="55c42-102">How to: Create Pre-Computed Tasks</span></span>
<span data-ttu-id="55c42-103">W tym dokumencie opisano sposób użycia <xref:System.Threading.Tasks.Task.FromResult%2A?displayProperty=nameWithType> metody do pobierania wyników asynchronicznych operacji pobierania przechowywanych w pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="55c42-103">This document describes how to use the <xref:System.Threading.Tasks.Task.FromResult%2A?displayProperty=nameWithType> method to retrieve the results of asynchronous download operations that are held in a cache.</span></span> <span data-ttu-id="55c42-104"><xref:System.Threading.Tasks.Task.FromResult%2A>Metoda zwraca gotowy <xref:System.Threading.Tasks.Task%601> obiekt, który posiada podaną wartość jako <xref:System.Threading.Tasks.Task%601.Result%2A> Właściwość.</span><span class="sxs-lookup"><span data-stu-id="55c42-104">The <xref:System.Threading.Tasks.Task.FromResult%2A> method returns a finished <xref:System.Threading.Tasks.Task%601> object that holds the provided value as its <xref:System.Threading.Tasks.Task%601.Result%2A> property.</span></span> <span data-ttu-id="55c42-105">Ta metoda jest przydatna w przypadku wykonywania operacji asynchronicznej, która zwraca <xref:System.Threading.Tasks.Task%601> obiekt, a wynik tego <xref:System.Threading.Tasks.Task%601> obiektu jest już obliczany.</span><span class="sxs-lookup"><span data-stu-id="55c42-105">This method is useful when you perform an asynchronous operation that returns a <xref:System.Threading.Tasks.Task%601> object, and the result of that <xref:System.Threading.Tasks.Task%601> object is already computed.</span></span>  
  
## <a name="example"></a><span data-ttu-id="55c42-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="55c42-106">Example</span></span>  
 <span data-ttu-id="55c42-107">Poniższy przykład pobiera ciągi z sieci Web.</span><span class="sxs-lookup"><span data-stu-id="55c42-107">The following example downloads strings from the web.</span></span> <span data-ttu-id="55c42-108">Definiuje `DownloadStringAsync` metodę.</span><span class="sxs-lookup"><span data-stu-id="55c42-108">It defines the `DownloadStringAsync` method.</span></span> <span data-ttu-id="55c42-109">Ta metoda umożliwia pobieranie ciągów z sieci Web asynchronicznie.</span><span class="sxs-lookup"><span data-stu-id="55c42-109">This method downloads strings from the web asynchronously.</span></span> <span data-ttu-id="55c42-110">Ten przykład używa również <xref:System.Collections.Concurrent.ConcurrentDictionary%602> obiektu do buforowania wyników poprzednich operacji.</span><span class="sxs-lookup"><span data-stu-id="55c42-110">This example also uses a <xref:System.Collections.Concurrent.ConcurrentDictionary%602> object to cache the results of previous operations.</span></span> <span data-ttu-id="55c42-111">Jeśli adres wejściowy jest przechowywany w tej pamięci podręcznej, `DownloadStringAsync` używa <xref:System.Threading.Tasks.Task.FromResult%2A> metody, aby utworzyć <xref:System.Threading.Tasks.Task%601> obiekt, który przechowuje zawartość pod tym adresem.</span><span class="sxs-lookup"><span data-stu-id="55c42-111">If the input address is held in this cache, `DownloadStringAsync` uses the <xref:System.Threading.Tasks.Task.FromResult%2A> method to produce a <xref:System.Threading.Tasks.Task%601> object that holds the content at that address.</span></span> <span data-ttu-id="55c42-112">W przeciwnym razie program `DownloadStringAsync` pobierze plik z sieci Web i doda wynik do pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="55c42-112">Otherwise, `DownloadStringAsync` downloads the file from the web and adds the result to the cache.</span></span>  
  
 [!code-csharp[TPL_CachedDownloads#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_cacheddownloads/cs/cacheddownloads.cs#1)]
 [!code-vb[TPL_CachedDownloads#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_cacheddownloads/vb/cacheddownloads.vb#1)]  
  
 <span data-ttu-id="55c42-113">Ten przykład oblicza czas wymagany do pobrania wielu ciągów dwa razy.</span><span class="sxs-lookup"><span data-stu-id="55c42-113">This example computes the time that is required to download multiple strings two times.</span></span> <span data-ttu-id="55c42-114">Drugi zestaw operacji pobierania powinien trwać krócej niż pierwszy zestaw, ponieważ wyniki są przechowywane w pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="55c42-114">The second set of download operations should take less time than the first set because the results are held in the cache.</span></span> <span data-ttu-id="55c42-115"><xref:System.Threading.Tasks.Task.FromResult%2A>Metoda umożliwia `DownloadStringAsync` metodzie tworzenie <xref:System.Threading.Tasks.Task%601> obiektów, które zawierają te wstępnie obliczone wyniki.</span><span class="sxs-lookup"><span data-stu-id="55c42-115">The <xref:System.Threading.Tasks.Task.FromResult%2A> method enables the `DownloadStringAsync` method to create <xref:System.Threading.Tasks.Task%601> objects that hold these pre-computed results.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="55c42-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="55c42-116">See also</span></span>

- [<span data-ttu-id="55c42-117">Programowanie asynchroniczne oparte na zadaniach</span><span class="sxs-lookup"><span data-stu-id="55c42-117">Task-based Asynchronous Programming</span></span>](task-based-asynchronous-programming.md)
