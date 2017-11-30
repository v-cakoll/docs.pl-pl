---
title: "Zły tryb pliku"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vbrID54
ms.assetid: 74891e96-884b-4c8d-872d-cd11ae272372
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: a540135727eb97f4df5027e2ded7271e21bb4648
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="bad-file-mode"></a><span data-ttu-id="34e53-102">Zły tryb pliku</span><span class="sxs-lookup"><span data-stu-id="34e53-102">Bad file mode</span></span>
<span data-ttu-id="34e53-103">Instrukcje używane w manipulowanie zawartością pliku musi być odpowiedni tryb, w którym plik został otwarty.</span><span class="sxs-lookup"><span data-stu-id="34e53-103">Statements used in manipulating file contents must be appropriate to the mode in which the file was opened.</span></span> <span data-ttu-id="34e53-104">Możliwe przyczyny:</span><span class="sxs-lookup"><span data-stu-id="34e53-104">Possible causes include:</span></span>  
  
-   <span data-ttu-id="34e53-105">A `FilePutObject` lub `FileGetObject` instrukcji określa plik sekwencyjnych.</span><span class="sxs-lookup"><span data-stu-id="34e53-105">A `FilePutObject` or `FileGetObject` statement specifies a sequential file.</span></span>  
  
-   <span data-ttu-id="34e53-106">A `Print` instrukcji określa plik otwarty w trybie dostępu innych niż `Output` lub `Append`.</span><span class="sxs-lookup"><span data-stu-id="34e53-106">A `Print` statement specifies a file opened for an access mode other than `Output` or `Append`.</span></span>  
  
-   <span data-ttu-id="34e53-107">`Input` Pliku otwartym w trybie dostępu do innych niż określa — instrukcja`Input`</span><span class="sxs-lookup"><span data-stu-id="34e53-107">An `Input` statement specifies a file opened for an access mode other than `Input`</span></span>  
  
-   <span data-ttu-id="34e53-108">Próba zapisu w pliku tylko do odczytu.</span><span class="sxs-lookup"><span data-stu-id="34e53-108">An attempt to write to a read-only file.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="34e53-109">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="34e53-109">To correct this error</span></span>  
  
-   <span data-ttu-id="34e53-110">Upewnij się, że `FilePutObject` i `FileGetObject` odnosi się tylko do plików Otwórz dla `Random` lub `Binary` dostępu.</span><span class="sxs-lookup"><span data-stu-id="34e53-110">Make sure `FilePutObject` and `FileGetObject` are only referring to files open for `Random` or `Binary` access.</span></span>  
  
-   <span data-ttu-id="34e53-111">Upewnij się, że `Print` Określa plik otwarty albo `Output` lub `Append` tryb dostępu.</span><span class="sxs-lookup"><span data-stu-id="34e53-111">Make sure `Print` specifies a file opened for either `Output` or `Append` access mode.</span></span> <span data-ttu-id="34e53-112">Jeśli nie, użyj innego instrukcji, aby umieścić dane w pliku lub plik otwarty w trybie odpowiednie.</span><span class="sxs-lookup"><span data-stu-id="34e53-112">If not, use a different statement to place data in the file, or reopen the file in an appropriate mode.</span></span>  
  
-   <span data-ttu-id="34e53-113">Upewnij się, że `Input` Określa plik otwarty do `Input`.</span><span class="sxs-lookup"><span data-stu-id="34e53-113">Make sure `Input` specifies a file opened for `Input`.</span></span> <span data-ttu-id="34e53-114">Jeśli nie, użyj innego instrukcji, aby umieścić w pliku danych lub Otwórz plik w odpowiedni tryb.</span><span class="sxs-lookup"><span data-stu-id="34e53-114">If not, use a different statement to place data in the file or reopen the file in an appropriate mode.</span></span>  
  
-   <span data-ttu-id="34e53-115">Podczas pisania w pliku tylko do odczytu, Zmień stan odczytu/zapisu pliku lub nie należy zapisywać do niego.</span><span class="sxs-lookup"><span data-stu-id="34e53-115">If you are writing to a read-only file, change the read/write status of the file or do not try to write to it.</span></span>  
  
-   <span data-ttu-id="34e53-116">Użyj funkcji dostępnych w `My.Computer.FileSystem` obiektu.</span><span class="sxs-lookup"><span data-stu-id="34e53-116">Use the functionality available in the `My.Computer.FileSystem` object.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="34e53-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="34e53-117">See Also</span></span>  
 <xref:Microsoft.VisualBasic.FileSystem>  
 [<span data-ttu-id="34e53-118">Rozwiązywanie problemów: Odczytywanie z oraz zapisywanie w plikach tekstowych</span><span class="sxs-lookup"><span data-stu-id="34e53-118">Troubleshooting: Reading from and Writing to Text Files</span></span>](../../../visual-basic/developing-apps/programming/drives-directories-files/troubleshooting-reading-from-and-writing-to-text-files.md)
