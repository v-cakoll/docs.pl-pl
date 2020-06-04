---
title: Zły tryb pliku
ms.date: 07/20/2015
f1_keywords:
- vbrID54
ms.assetid: 74891e96-884b-4c8d-872d-cd11ae272372
ms.openlocfilehash: 534ea2d8316dc29cace798c5ad9b7697a290026f
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84409872"
---
# <a name="bad-file-mode"></a><span data-ttu-id="83d78-102">Zły tryb pliku</span><span class="sxs-lookup"><span data-stu-id="83d78-102">Bad file mode</span></span>
<span data-ttu-id="83d78-103">Instrukcje używane podczas manipulowania zawartością pliku muszą być odpowiednie dla trybu, w którym plik został otwarty.</span><span class="sxs-lookup"><span data-stu-id="83d78-103">Statements used in manipulating file contents must be appropriate to the mode in which the file was opened.</span></span> <span data-ttu-id="83d78-104">Możliwe przyczyny są następujące:</span><span class="sxs-lookup"><span data-stu-id="83d78-104">Possible causes include:</span></span>  
  
- <span data-ttu-id="83d78-105">`FilePutObject`Instrukcja or `FileGetObject` określa sekwencyjny plik.</span><span class="sxs-lookup"><span data-stu-id="83d78-105">A `FilePutObject` or `FileGetObject` statement specifies a sequential file.</span></span>  
  
- <span data-ttu-id="83d78-106">`Print`Instrukcja Określa plik otwarty dla trybu dostępu innego niż `Output` lub `Append` .</span><span class="sxs-lookup"><span data-stu-id="83d78-106">A `Print` statement specifies a file opened for an access mode other than `Output` or `Append`.</span></span>  
  
- <span data-ttu-id="83d78-107">`Input`Instrukcja Określa plik otwarty dla trybu dostępu innego niż`Input`</span><span class="sxs-lookup"><span data-stu-id="83d78-107">An `Input` statement specifies a file opened for an access mode other than `Input`</span></span>  
  
- <span data-ttu-id="83d78-108">Próba zapisu w pliku tylko do odczytu.</span><span class="sxs-lookup"><span data-stu-id="83d78-108">An attempt to write to a read-only file.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="83d78-109">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="83d78-109">To correct this error</span></span>  
  
- <span data-ttu-id="83d78-110">Upewnij się `FilePutObject` , że `FileGetObject` odwołują się tylko do plików otwartych dla programu `Random` lub `Binary` .</span><span class="sxs-lookup"><span data-stu-id="83d78-110">Make sure `FilePutObject` and `FileGetObject` are only referring to files open for `Random` or `Binary` access.</span></span>  
  
- <span data-ttu-id="83d78-111">Upewnij się, że `Print` określony plik jest otwarty w `Output` trybie obu lub `Append` dostępu.</span><span class="sxs-lookup"><span data-stu-id="83d78-111">Make sure `Print` specifies a file opened for either `Output` or `Append` access mode.</span></span> <span data-ttu-id="83d78-112">Jeśli nie, użyj innej instrukcji, aby umieścić dane w pliku, lub Otwórz ponownie plik w odpowiednim trybie.</span><span class="sxs-lookup"><span data-stu-id="83d78-112">If not, use a different statement to place data in the file, or reopen the file in an appropriate mode.</span></span>  
  
- <span data-ttu-id="83d78-113">Upewnij się `Input` , że wybrano plik otwarty dla programu `Input` .</span><span class="sxs-lookup"><span data-stu-id="83d78-113">Make sure `Input` specifies a file opened for `Input`.</span></span> <span data-ttu-id="83d78-114">Jeśli nie, użyj innej instrukcji, aby umieścić dane w pliku, lub Otwórz ponownie plik w odpowiednim trybie.</span><span class="sxs-lookup"><span data-stu-id="83d78-114">If not, use a different statement to place data in the file or reopen the file in an appropriate mode.</span></span>  
  
- <span data-ttu-id="83d78-115">Jeśli zapisujesz do pliku tylko do odczytu, Zmień stan odczytu/zapisu pliku lub nie próbuj zapisywać do niego.</span><span class="sxs-lookup"><span data-stu-id="83d78-115">If you are writing to a read-only file, change the read/write status of the file or do not try to write to it.</span></span>  
  
- <span data-ttu-id="83d78-116">Użyj funkcji dostępnych w `My.Computer.FileSystem` obiekcie.</span><span class="sxs-lookup"><span data-stu-id="83d78-116">Use the functionality available in the `My.Computer.FileSystem` object.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="83d78-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="83d78-117">See also</span></span>

- <xref:Microsoft.VisualBasic.FileSystem>
- [<span data-ttu-id="83d78-118">Rozwiązywanie problemów: Odczytywanie z plików tekstowych oraz zapisywanie w nich</span><span class="sxs-lookup"><span data-stu-id="83d78-118">Troubleshooting: Reading from and Writing to Text Files</span></span>](../../developing-apps/programming/drives-directories-files/troubleshooting-reading-from-and-writing-to-text-files.md)
