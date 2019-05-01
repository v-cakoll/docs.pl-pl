---
title: Zły tryb pliku
ms.date: 07/20/2015
f1_keywords:
- vbrID54
ms.assetid: 74891e96-884b-4c8d-872d-cd11ae272372
ms.openlocfilehash: d3d0ebd003f178567ec9e9b19d6baccb8bc15f60
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61935242"
---
# <a name="bad-file-mode"></a><span data-ttu-id="4b4bb-102">Zły tryb pliku</span><span class="sxs-lookup"><span data-stu-id="4b4bb-102">Bad file mode</span></span>
<span data-ttu-id="4b4bb-103">Instrukcje używane w manipulowanie zawartością pliku musi być zgodna z trybem, w którym plik został otwarty.</span><span class="sxs-lookup"><span data-stu-id="4b4bb-103">Statements used in manipulating file contents must be appropriate to the mode in which the file was opened.</span></span> <span data-ttu-id="4b4bb-104">Możliwe przyczyny:</span><span class="sxs-lookup"><span data-stu-id="4b4bb-104">Possible causes include:</span></span>  
  
- <span data-ttu-id="4b4bb-105">A `FilePutObject` lub `FileGetObject` instrukcja Określa kolejny plik.</span><span class="sxs-lookup"><span data-stu-id="4b4bb-105">A `FilePutObject` or `FileGetObject` statement specifies a sequential file.</span></span>  
  
- <span data-ttu-id="4b4bb-106">A `Print` instrukcja Określa plik, który został otwarty w trybie dostępu innych niż `Output` lub `Append`.</span><span class="sxs-lookup"><span data-stu-id="4b4bb-106">A `Print` statement specifies a file opened for an access mode other than `Output` or `Append`.</span></span>  
  
- <span data-ttu-id="4b4bb-107">`Input` Instrukcja Określa plik, który został otwarty inny niż tryb dostępu `Input`</span><span class="sxs-lookup"><span data-stu-id="4b4bb-107">An `Input` statement specifies a file opened for an access mode other than `Input`</span></span>  
  
- <span data-ttu-id="4b4bb-108">Próba zapisu do plików tylko do odczytu.</span><span class="sxs-lookup"><span data-stu-id="4b4bb-108">An attempt to write to a read-only file.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="4b4bb-109">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="4b4bb-109">To correct this error</span></span>  
  
- <span data-ttu-id="4b4bb-110">Upewnij się, że `FilePutObject` i `FileGetObject` odnoszą się tylko do plików otwartych do `Random` lub `Binary` dostępu.</span><span class="sxs-lookup"><span data-stu-id="4b4bb-110">Make sure `FilePutObject` and `FileGetObject` are only referring to files open for `Random` or `Binary` access.</span></span>  
  
- <span data-ttu-id="4b4bb-111">Upewnij się, że `Print` Określa plik, który został otwarty albo `Output` lub `Append` tryb dostępu.</span><span class="sxs-lookup"><span data-stu-id="4b4bb-111">Make sure `Print` specifies a file opened for either `Output` or `Append` access mode.</span></span> <span data-ttu-id="4b4bb-112">W przeciwnym razie użyj innej instrukcji, aby umieścić dane w pliku, lub ponownie otworzyć plik w odpowiedni tryb.</span><span class="sxs-lookup"><span data-stu-id="4b4bb-112">If not, use a different statement to place data in the file, or reopen the file in an appropriate mode.</span></span>  
  
- <span data-ttu-id="4b4bb-113">Upewnij się, że `Input` Określa plik, który został otwarty `Input`.</span><span class="sxs-lookup"><span data-stu-id="4b4bb-113">Make sure `Input` specifies a file opened for `Input`.</span></span> <span data-ttu-id="4b4bb-114">W przeciwnym razie użyj innej instrukcji, aby umieścić dane w pliku lub ponownie otworzyć plik w odpowiedni tryb.</span><span class="sxs-lookup"><span data-stu-id="4b4bb-114">If not, use a different statement to place data in the file or reopen the file in an appropriate mode.</span></span>  
  
- <span data-ttu-id="4b4bb-115">Jeśli piszesz w pliku tylko do odczytu, Zmień stan odczytu/zapisu pliku lub nie należy próbować zapisanie w nim.</span><span class="sxs-lookup"><span data-stu-id="4b4bb-115">If you are writing to a read-only file, change the read/write status of the file or do not try to write to it.</span></span>  
  
- <span data-ttu-id="4b4bb-116">Użyj funkcji dostępnych w `My.Computer.FileSystem` obiektu.</span><span class="sxs-lookup"><span data-stu-id="4b4bb-116">Use the functionality available in the `My.Computer.FileSystem` object.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4b4bb-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="4b4bb-117">See also</span></span>

- <xref:Microsoft.VisualBasic.FileSystem>
- [<span data-ttu-id="4b4bb-118">Rozwiązywanie problemów: Odczytywanie z oraz zapisywanie w plikach tekstowych</span><span class="sxs-lookup"><span data-stu-id="4b4bb-118">Troubleshooting: Reading from and Writing to Text Files</span></span>](../../../visual-basic/developing-apps/programming/drives-directories-files/troubleshooting-reading-from-and-writing-to-text-files.md)
