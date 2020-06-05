---
title: Nie można ustawić wartości Nothing dla kodowania
ms.date: 07/20/2015
ms.assetid: 59f7c731-8291-4a85-bf51-c225e48cdc84
ms.openlocfilehash: 41565d1aa3b69f6ad92d4bbf2b2f2170014aef87
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84394482"
---
# <a name="encoding-cannot-be-set-to-nothing"></a><span data-ttu-id="cf631-102">Nie można ustawić wartości Nothing dla kodowania</span><span class="sxs-lookup"><span data-stu-id="cf631-102">Encoding cannot be set to Nothing</span></span>
<span data-ttu-id="cf631-103">Próba odczytu z pliku lub zapisu do niego nie powiodła się, ponieważ parametr został `encoding` ustawiony na `Nothing` wartość, ale wymaga prawidłowej wartości.</span><span class="sxs-lookup"><span data-stu-id="cf631-103">An attempt to read from or write to a file has failed because the parameter `encoding` has been set to `Nothing` but requires a valid value.</span></span>  
  
 <span data-ttu-id="cf631-104"><xref:System.Text.Encoding>służy do określania kodowania, które ma być używane podczas zapisywania w pliku.</span><span class="sxs-lookup"><span data-stu-id="cf631-104"><xref:System.Text.Encoding> is used to determine what encoding to use when writing to a file.</span></span> <span data-ttu-id="cf631-105">Domyślnym ustawieniem jest UTF-8.</span><span class="sxs-lookup"><span data-stu-id="cf631-105">The default is UTF-8.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="cf631-106">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="cf631-106">To correct this error</span></span>  
  
- <span data-ttu-id="cf631-107">Podaj prawidłową wartość `encoding` parametru.</span><span class="sxs-lookup"><span data-stu-id="cf631-107">Supply a valid value for the `encoding` parameter.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cf631-108">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="cf631-108">See also</span></span>

- [<span data-ttu-id="cf631-109">Kodowanie pliku</span><span class="sxs-lookup"><span data-stu-id="cf631-109">File Encodings</span></span>](../developing-apps/programming/drives-directories-files/file-encodings.md)
- [<span data-ttu-id="cf631-110">Odczyt z plików</span><span class="sxs-lookup"><span data-stu-id="cf631-110">Reading from Files</span></span>](../developing-apps/programming/drives-directories-files/reading-from-files.md)
- [<span data-ttu-id="cf631-111">Zapisywanie w plikach</span><span class="sxs-lookup"><span data-stu-id="cf631-111">Writing to Files</span></span>](../developing-apps/programming/drives-directories-files/writing-to-files.md)
- [<span data-ttu-id="cf631-112">My. Computer. FileSystem. ReadAllText obiektu</span><span class="sxs-lookup"><span data-stu-id="cf631-112">My.Computer.FileSystem.ReadAllText</span></span>](xref:Microsoft.VisualBasic.FileIO.FileSystem.ReadAllText%2A)
- [<span data-ttu-id="cf631-113">My. Computer. FileSystem. WriteAllText —</span><span class="sxs-lookup"><span data-stu-id="cf631-113">My.Computer.FileSystem.WriteAllText</span></span>](xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllText%2A)
