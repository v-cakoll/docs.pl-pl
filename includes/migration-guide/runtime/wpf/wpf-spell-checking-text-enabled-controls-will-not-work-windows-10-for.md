---
ms.openlocfilehash: abb89099c4c8a5d9c0e55ef8f357faf44e75b045
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59774212"
---
### <a name="wpf-spell-checking-in-text-enabled-controls-will-not-work-in-windows-10-for-languages-not-in-the-oss-input-language-list"></a><span data-ttu-id="dfa43-101">WPF sprawdzanie pisowni w włączona tekst kontrolki nie będzie działać w systemie Windows 10 dla języków nie ma na liście język systemu operacyjnego</span><span class="sxs-lookup"><span data-stu-id="dfa43-101">WPF spell checking in text-enabled controls will not work in Windows 10 for languages not in the OS's input language list</span></span>

|   |   |
|---|---|
|<span data-ttu-id="dfa43-102">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="dfa43-102">Details</span></span>|<span data-ttu-id="dfa43-103">Moduł sprawdzania pisowni uruchomiony w systemie Windows 10, mogą nie działać dla kontrolek WPF z komputerów z obsługą tekstu możliwości sprawdzania pisowni platformy nie są dostępne tylko dla języków występuje na liście języków. W systemie Windows 10 gdy język jest dodawany do listy dostępnych klawiatury Windows automatycznie pobiorą i zainstalują odpowiedniej funkcji pakietu żądanie (FDZ), która oferuje możliwości sprawdzania pisowni.</span><span class="sxs-lookup"><span data-stu-id="dfa43-103">When running on Windows 10, the spell checker may not work for WPF text-enabled controls because platform spell-checking capabilities are available only for languages present in the input languages list.In Windows 10, when a language is added to the list of available keyboards, Windows automatically downloads and installs a corresponding Feature on Demand (FOD) package that provides spell-checking capabilities.</span></span> <span data-ttu-id="dfa43-104">Dodając język do listy języków, będzie objęta sprawdzania pisowni.</span><span class="sxs-lookup"><span data-stu-id="dfa43-104">By adding the language to the input languages list, the spell checker will be supported.</span></span>|
|<span data-ttu-id="dfa43-105">Sugestia</span><span class="sxs-lookup"><span data-stu-id="dfa43-105">Suggestion</span></span>|<span data-ttu-id="dfa43-106">Należy pamiętać, że język lub tekst ma być sprawdzana pisownia należy dodać język do sprawdzania pisowni do pracy w systemie Windows 10.</span><span class="sxs-lookup"><span data-stu-id="dfa43-106">Be aware that the language or text to be spell-checked must be added as an input language for spell-checking to work in Windows 10.</span></span>|
|<span data-ttu-id="dfa43-107">Zakres</span><span class="sxs-lookup"><span data-stu-id="dfa43-107">Scope</span></span>|<span data-ttu-id="dfa43-108">Krawędź</span><span class="sxs-lookup"><span data-stu-id="dfa43-108">Edge</span></span>|
|<span data-ttu-id="dfa43-109">Wersja</span><span class="sxs-lookup"><span data-stu-id="dfa43-109">Version</span></span>|<span data-ttu-id="dfa43-110">4.6</span><span class="sxs-lookup"><span data-stu-id="dfa43-110">4.6</span></span>|
|<span data-ttu-id="dfa43-111">Typ</span><span class="sxs-lookup"><span data-stu-id="dfa43-111">Type</span></span>|<span data-ttu-id="dfa43-112">Środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="dfa43-112">Runtime</span></span>|
