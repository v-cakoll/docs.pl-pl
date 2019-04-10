---
ms.openlocfilehash: abb89099c4c8a5d9c0e55ef8f357faf44e75b045
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59234193"
---
### <a name="wpf-spell-checking-in-text-enabled-controls-will-not-work-in-windows-10-for-languages-not-in-the-oss-input-language-list"></a><span data-ttu-id="a5af0-101">WPF sprawdzanie pisowni w włączona tekst kontrolki nie będzie działać w systemie Windows 10 dla języków nie ma na liście język systemu operacyjnego</span><span class="sxs-lookup"><span data-stu-id="a5af0-101">WPF spell checking in text-enabled controls will not work in Windows 10 for languages not in the OS's input language list</span></span>

|   |   |
|---|---|
|<span data-ttu-id="a5af0-102">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="a5af0-102">Details</span></span>|<span data-ttu-id="a5af0-103">Moduł sprawdzania pisowni uruchomiony w systemie Windows 10, mogą nie działać dla kontrolek WPF z komputerów z obsługą tekstu możliwości sprawdzania pisowni platformy nie są dostępne tylko dla języków występuje na liście języków. W systemie Windows 10 gdy język jest dodawany do listy dostępnych klawiatury Windows automatycznie pobiorą i zainstalują odpowiedniej funkcji pakietu żądanie (FDZ), która oferuje możliwości sprawdzania pisowni.</span><span class="sxs-lookup"><span data-stu-id="a5af0-103">When running on Windows 10, the spell checker may not work for WPF text-enabled controls because platform spell-checking capabilities are available only for languages present in the input languages list.In Windows 10, when a language is added to the list of available keyboards, Windows automatically downloads and installs a corresponding Feature on Demand (FOD) package that provides spell-checking capabilities.</span></span> <span data-ttu-id="a5af0-104">Dodając język do listy języków, będzie objęta sprawdzania pisowni.</span><span class="sxs-lookup"><span data-stu-id="a5af0-104">By adding the language to the input languages list, the spell checker will be supported.</span></span>|
|<span data-ttu-id="a5af0-105">Sugestia</span><span class="sxs-lookup"><span data-stu-id="a5af0-105">Suggestion</span></span>|<span data-ttu-id="a5af0-106">Należy pamiętać, że język lub tekst ma być sprawdzana pisownia należy dodać język do sprawdzania pisowni do pracy w systemie Windows 10.</span><span class="sxs-lookup"><span data-stu-id="a5af0-106">Be aware that the language or text to be spell-checked must be added as an input language for spell-checking to work in Windows 10.</span></span>|
|<span data-ttu-id="a5af0-107">Zakres</span><span class="sxs-lookup"><span data-stu-id="a5af0-107">Scope</span></span>|<span data-ttu-id="a5af0-108">Krawędź</span><span class="sxs-lookup"><span data-stu-id="a5af0-108">Edge</span></span>|
|<span data-ttu-id="a5af0-109">Wersja</span><span class="sxs-lookup"><span data-stu-id="a5af0-109">Version</span></span>|<span data-ttu-id="a5af0-110">4.6</span><span class="sxs-lookup"><span data-stu-id="a5af0-110">4.6</span></span>|
|<span data-ttu-id="a5af0-111">Typ</span><span class="sxs-lookup"><span data-stu-id="a5af0-111">Type</span></span>|<span data-ttu-id="a5af0-112">Środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="a5af0-112">Runtime</span></span>|
