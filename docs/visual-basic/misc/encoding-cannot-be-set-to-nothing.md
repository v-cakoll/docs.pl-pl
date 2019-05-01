---
title: Kodowanie nie można ustawić na wartość Nothing
ms.date: 07/20/2015
ms.assetid: 59f7c731-8291-4a85-bf51-c225e48cdc84
ms.openlocfilehash: 30b0b4a29fbdf931aa62263b75d1fa946e87b145
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61970329"
---
# <a name="encoding-cannot-be-set-to-nothing"></a><span data-ttu-id="0b8ca-102">Kodowanie nie można ustawić na wartość Nothing</span><span class="sxs-lookup"><span data-stu-id="0b8ca-102">Encoding cannot be set to Nothing</span></span>
<span data-ttu-id="0b8ca-103">Podjęto próbę odczytu z lub zapisu w pliku nie powiodło się, ponieważ parametr `encoding` został ustawiony na `Nothing` , ale wymaga prawidłowej wartości.</span><span class="sxs-lookup"><span data-stu-id="0b8ca-103">An attempt to read from or write to a file has failed because the parameter `encoding` has been set to `Nothing` but requires a valid value.</span></span>  
  
 <span data-ttu-id="0b8ca-104"><xref:System.Text.Encoding> Służy do określenia, jakie szyfrowanie do użycia podczas zapisywania do pliku.</span><span class="sxs-lookup"><span data-stu-id="0b8ca-104"><xref:System.Text.Encoding> is used to determine what encoding to use when writing to a file.</span></span> <span data-ttu-id="0b8ca-105">Wartość domyślna to UTF-8.</span><span class="sxs-lookup"><span data-stu-id="0b8ca-105">The default is UTF-8.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="0b8ca-106">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="0b8ca-106">To correct this error</span></span>  
  
- <span data-ttu-id="0b8ca-107">Podaj prawidłową wartość dla `encoding` parametru.</span><span class="sxs-lookup"><span data-stu-id="0b8ca-107">Supply a valid value for the `encoding` parameter.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0b8ca-108">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="0b8ca-108">See also</span></span>

- [<span data-ttu-id="0b8ca-109">Kodowanie pliku</span><span class="sxs-lookup"><span data-stu-id="0b8ca-109">File Encodings</span></span>](../../visual-basic/developing-apps/programming/drives-directories-files/file-encodings.md)
- [<span data-ttu-id="0b8ca-110">Odczyt z plików</span><span class="sxs-lookup"><span data-stu-id="0b8ca-110">Reading from Files</span></span>](../../visual-basic/developing-apps/programming/drives-directories-files/reading-from-files.md)
- [<span data-ttu-id="0b8ca-111">Zapisywanie w plikach</span><span class="sxs-lookup"><span data-stu-id="0b8ca-111">Writing to Files</span></span>](../../visual-basic/developing-apps/programming/drives-directories-files/writing-to-files.md)
- [<span data-ttu-id="0b8ca-112">My.Computer.FileSystem.ReadAllText</span><span class="sxs-lookup"><span data-stu-id="0b8ca-112">My.Computer.FileSystem.ReadAllText</span></span>](xref:Microsoft.VisualBasic.FileIO.FileSystem.ReadAllText%2A)
- [<span data-ttu-id="0b8ca-113">My.Computer.FileSystem.WriteAllText</span><span class="sxs-lookup"><span data-stu-id="0b8ca-113">My.Computer.FileSystem.WriteAllText</span></span>](xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllText%2A)
