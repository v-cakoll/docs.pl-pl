---
title: Zły tryb pliku
ms.date: 07/20/2015
f1_keywords:
- vbrID54
ms.assetid: 74891e96-884b-4c8d-872d-cd11ae272372
ms.openlocfilehash: 9a59faf1b6f845858e36efcabdf0758e41ad75dc
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64619746"
---
# <a name="bad-file-mode"></a><span data-ttu-id="d8a68-102">Zły tryb pliku</span><span class="sxs-lookup"><span data-stu-id="d8a68-102">Bad file mode</span></span>
<span data-ttu-id="d8a68-103">Instrukcje używane w manipulowanie zawartością pliku musi być zgodna z trybem, w którym plik został otwarty.</span><span class="sxs-lookup"><span data-stu-id="d8a68-103">Statements used in manipulating file contents must be appropriate to the mode in which the file was opened.</span></span> <span data-ttu-id="d8a68-104">Możliwe przyczyny:</span><span class="sxs-lookup"><span data-stu-id="d8a68-104">Possible causes include:</span></span>  
  
- <span data-ttu-id="d8a68-105">A `FilePutObject` lub `FileGetObject` instrukcja Określa kolejny plik.</span><span class="sxs-lookup"><span data-stu-id="d8a68-105">A `FilePutObject` or `FileGetObject` statement specifies a sequential file.</span></span>  
  
- <span data-ttu-id="d8a68-106">A `Print` instrukcja Określa plik, który został otwarty w trybie dostępu innych niż `Output` lub `Append`.</span><span class="sxs-lookup"><span data-stu-id="d8a68-106">A `Print` statement specifies a file opened for an access mode other than `Output` or `Append`.</span></span>  
  
- <span data-ttu-id="d8a68-107">`Input` Instrukcja Określa plik, który został otwarty inny niż tryb dostępu `Input`</span><span class="sxs-lookup"><span data-stu-id="d8a68-107">An `Input` statement specifies a file opened for an access mode other than `Input`</span></span>  
  
- <span data-ttu-id="d8a68-108">Próba zapisu do plików tylko do odczytu.</span><span class="sxs-lookup"><span data-stu-id="d8a68-108">An attempt to write to a read-only file.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="d8a68-109">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="d8a68-109">To correct this error</span></span>  
  
- <span data-ttu-id="d8a68-110">Upewnij się, że `FilePutObject` i `FileGetObject` odnoszą się tylko do plików otwartych do `Random` lub `Binary` dostępu.</span><span class="sxs-lookup"><span data-stu-id="d8a68-110">Make sure `FilePutObject` and `FileGetObject` are only referring to files open for `Random` or `Binary` access.</span></span>  
  
- <span data-ttu-id="d8a68-111">Upewnij się, że `Print` Określa plik, który został otwarty albo `Output` lub `Append` tryb dostępu.</span><span class="sxs-lookup"><span data-stu-id="d8a68-111">Make sure `Print` specifies a file opened for either `Output` or `Append` access mode.</span></span> <span data-ttu-id="d8a68-112">W przeciwnym razie użyj innej instrukcji, aby umieścić dane w pliku, lub ponownie otworzyć plik w odpowiedni tryb.</span><span class="sxs-lookup"><span data-stu-id="d8a68-112">If not, use a different statement to place data in the file, or reopen the file in an appropriate mode.</span></span>  
  
- <span data-ttu-id="d8a68-113">Upewnij się, że `Input` Określa plik, który został otwarty `Input`.</span><span class="sxs-lookup"><span data-stu-id="d8a68-113">Make sure `Input` specifies a file opened for `Input`.</span></span> <span data-ttu-id="d8a68-114">W przeciwnym razie użyj innej instrukcji, aby umieścić dane w pliku lub ponownie otworzyć plik w odpowiedni tryb.</span><span class="sxs-lookup"><span data-stu-id="d8a68-114">If not, use a different statement to place data in the file or reopen the file in an appropriate mode.</span></span>  
  
- <span data-ttu-id="d8a68-115">Jeśli piszesz w pliku tylko do odczytu, Zmień stan odczytu/zapisu pliku lub nie należy próbować zapisanie w nim.</span><span class="sxs-lookup"><span data-stu-id="d8a68-115">If you are writing to a read-only file, change the read/write status of the file or do not try to write to it.</span></span>  
  
- <span data-ttu-id="d8a68-116">Użyj funkcji dostępnych w `My.Computer.FileSystem` obiektu.</span><span class="sxs-lookup"><span data-stu-id="d8a68-116">Use the functionality available in the `My.Computer.FileSystem` object.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d8a68-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d8a68-117">See also</span></span>

- <xref:Microsoft.VisualBasic.FileSystem>
- [<span data-ttu-id="d8a68-118">Rozwiązywanie problemów: Odczytywanie z oraz zapisywanie w plikach tekstowych</span><span class="sxs-lookup"><span data-stu-id="d8a68-118">Troubleshooting: Reading from and Writing to Text Files</span></span>](../../../visual-basic/developing-apps/programming/drives-directories-files/troubleshooting-reading-from-and-writing-to-text-files.md)
