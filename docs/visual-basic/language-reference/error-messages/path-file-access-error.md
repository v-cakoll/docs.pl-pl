---
title: Błąd dostępu do ścieżki / pliku
ms.date: 07/20/2015
f1_keywords:
- vbrID75
ms.assetid: 6ce3a161-7316-46bd-a785-0d50e5414020
ms.openlocfilehash: 4f18c9216aa24840bc205534a97124d12698cb98
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59342157"
---
# <a name="pathfile-access-error"></a><span data-ttu-id="8ec5e-102">Błąd dostępu do ścieżki/pliku</span><span class="sxs-lookup"><span data-stu-id="8ec5e-102">Path/File access error</span></span>
<span data-ttu-id="8ec5e-103">Podczas operacji uzyskiwania dostępu do plików lub dostępu do dysku systemu operacyjnego nie można ustanowić połączenia między ścieżkę i nazwę pliku.</span><span class="sxs-lookup"><span data-stu-id="8ec5e-103">During a file-access or disk-access operation, the operating system could not make a connection between the path and the file name.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="8ec5e-104">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="8ec5e-104">To correct this error</span></span>  
  
1. <span data-ttu-id="8ec5e-105">Upewnij się, że specyfikacja plików jest poprawnie sformatowana.</span><span class="sxs-lookup"><span data-stu-id="8ec5e-105">Make sure the file specification is correctly formatted.</span></span> <span data-ttu-id="8ec5e-106">Nazwa pliku może zawierać w pełni kwalifikowana (bezwzględny) lub względny ścieżki.</span><span class="sxs-lookup"><span data-stu-id="8ec5e-106">A file name can contain a fully qualified (absolute) or relative path.</span></span> <span data-ttu-id="8ec5e-107">W pełni kwalifikowana ścieżka zaczyna się od nazwy dysku (Jeśli ścieżka znajduje się na innym dysku) i wyświetla jawna ścieżka z katalogu głównego, do pliku.</span><span class="sxs-lookup"><span data-stu-id="8ec5e-107">A fully qualified path starts with the drive name (if the path is on another drive) and lists the explicit path from the root to the file.</span></span> <span data-ttu-id="8ec5e-108">Dowolną ścieżkę, która nie jest w pełni kwalifikowany jest określana względem bieżącego dysku i katalogu.</span><span class="sxs-lookup"><span data-stu-id="8ec5e-108">Any path that is not fully qualified is relative to the current drive and directory.</span></span>  
  
2. <span data-ttu-id="8ec5e-109">Upewnij się, że użytkownik nie podjęła próby zapisania pliku, który zastąpi istniejący plik tylko do odczytu.</span><span class="sxs-lookup"><span data-stu-id="8ec5e-109">Make sure that you did not attempt to save a file that would replace an existing read-only file.</span></span> <span data-ttu-id="8ec5e-110">Jeśli jest to możliwe, zmień atrybut tylko do odczytu pliku docelowego lub zapisać plik pod inną nazwą pliku.</span><span class="sxs-lookup"><span data-stu-id="8ec5e-110">If this is the case, change the read-only attribute of the target file, or save the file with a different file name.</span></span>  
  
3. <span data-ttu-id="8ec5e-111">Upewnij się, że nie podjęła próby otwarcia pliku tylko do odczytu w kolejnych `Output` lub `Append` trybu.</span><span class="sxs-lookup"><span data-stu-id="8ec5e-111">Make sure you did not attempt to open a read-only file in sequential `Output` or `Append` mode.</span></span> <span data-ttu-id="8ec5e-112">Jeśli jest to możliwe, otwórz plik w `Input` tryb lub zmień atrybut tylko do odczytu pliku.</span><span class="sxs-lookup"><span data-stu-id="8ec5e-112">If this is the case, open the file in `Input` mode or change the read-only attribute of the file.</span></span>  
  
4. <span data-ttu-id="8ec5e-113">Upewnij się, że nie podjęła próby zmiany w projektach Visual Basic w bazie danych lub dokumentu.</span><span class="sxs-lookup"><span data-stu-id="8ec5e-113">Make sure you did not attempt to change a Visual Basic project within a database or document.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8ec5e-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8ec5e-114">See also</span></span>

- [<span data-ttu-id="8ec5e-115">Typy błędów</span><span class="sxs-lookup"><span data-stu-id="8ec5e-115">Error Types</span></span>](../../../visual-basic/programming-guide/language-features/error-types.md)
