---
ms.openlocfilehash: 1d2e4a058008676c6ea85becebd4bb9220569ef3
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621361"
---
### <a name="wpf-spell-checking-in-text-enabled-controls-will-not-work-in-windows-10-for-languages-not-in-the-oss-input-language-list"></a><span data-ttu-id="cdb29-101">Sprawdzanie pisowni WPF w kontrolkach z obsługą tekstu nie będzie działało w systemie Windows 10 dla języków, które nie są na liście języków wejściowych systemu operacyjnego</span><span class="sxs-lookup"><span data-stu-id="cdb29-101">WPF spell checking in text-enabled controls will not work in Windows 10 for languages not in the OS's input language list</span></span>

#### <a name="details"></a><span data-ttu-id="cdb29-102">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="cdb29-102">Details</span></span>

<span data-ttu-id="cdb29-103">W przypadku uruchamiania w systemie Windows 10 sprawdzanie pisowni może nie działać w przypadku kontrolek z obsługą tekstu WPF, ponieważ możliwości sprawdzania pisowni platformy są dostępne tylko dla języków znajdujących się na liście języków wejściowych. W systemie Windows 10 po dodaniu języka do listy dostępnych klawiatur system Windows automatycznie pobiera i instaluje odpowiedni pakiet funkcji na żądanie (FDZ), który zapewnia możliwości sprawdzania pisowni.</span><span class="sxs-lookup"><span data-stu-id="cdb29-103">When running on Windows 10, the spell checker may not work for WPF text-enabled controls because platform spell-checking capabilities are available only for languages present in the input languages list.In Windows 10, when a language is added to the list of available keyboards, Windows automatically downloads and installs a corresponding Feature on Demand (FOD) package that provides spell-checking capabilities.</span></span> <span data-ttu-id="cdb29-104">Po dodaniu języka do listy języków wejściowych sprawdzanie pisowni będzie obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="cdb29-104">By adding the language to the input languages list, the spell checker will be supported.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="cdb29-105">Sugestia</span><span class="sxs-lookup"><span data-stu-id="cdb29-105">Suggestion</span></span>

<span data-ttu-id="cdb29-106">Należy pamiętać, że język lub tekst do sprawdzenia pisowni należy dodać jako język wejściowy do sprawdzania pisowni w systemie Windows 10.</span><span class="sxs-lookup"><span data-stu-id="cdb29-106">Be aware that the language or text to be spell-checked must be added as an input language for spell-checking to work in Windows 10.</span></span>

| <span data-ttu-id="cdb29-107">Nazwa</span><span class="sxs-lookup"><span data-stu-id="cdb29-107">Name</span></span>    | <span data-ttu-id="cdb29-108">Wartość</span><span class="sxs-lookup"><span data-stu-id="cdb29-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="cdb29-109">Zakres</span><span class="sxs-lookup"><span data-stu-id="cdb29-109">Scope</span></span>   |<span data-ttu-id="cdb29-110">Brzeg</span><span class="sxs-lookup"><span data-stu-id="cdb29-110">Edge</span></span>|
|<span data-ttu-id="cdb29-111">Wersja</span><span class="sxs-lookup"><span data-stu-id="cdb29-111">Version</span></span>|<span data-ttu-id="cdb29-112">4.6</span><span class="sxs-lookup"><span data-stu-id="cdb29-112">4.6</span></span>|
|<span data-ttu-id="cdb29-113">Typ</span><span class="sxs-lookup"><span data-stu-id="cdb29-113">Type</span></span>|<span data-ttu-id="cdb29-114">Środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="cdb29-114">Runtime</span></span>|
