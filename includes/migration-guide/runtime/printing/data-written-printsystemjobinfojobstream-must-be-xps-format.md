---
ms.openlocfilehash: a007022bf32ffe76861f6f9016a7edace17b0f61
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620357"
---
### <a name="data-written-to-printsystemjobinfojobstream-must-be-in-xps-format"></a>Dane zapisywane do PrintSystemJobInfo. strumienia zadań muszą być w formacie XPS

#### <a name="details"></a>Szczegóły

<xref:System.Printing.PrintSystemJobInfo.JobStream>Właściwość uwidacznia strumień zadania drukowania. Użytkownik może wysyłać pierwotne dane do podstawowych składników drukowania systemu operacyjnego przez zapis do tego strumienia. Począwszy od .NET Framework 4,5 w systemie Windows 8 i nowszych wersjach systemu operacyjnego Windows, dane zapisywane w tym strumieniu muszą być w formacie XPS jako strumień pakietu.

#### <a name="suggestion"></a>Sugestia

Aby wydrukować zawartość wyjściową, można wykonać jedną z następujących czynności:<ul><li>Użyj <xref:System.Windows.Xps.XpsDocumentWriter> klasy do wyjściowej zawartości wydruku. Jest to zalecana alternatywa.</li><li>Upewnij się, że dane wysyłane do strumienia zwróconego przez <xref:System.Printing.PrintSystemJobInfo.JobStream> Właściwość są w formacie XPS jako strumień pakietu.</li></ul>

| Nazwa    | Wartość       |
|:--------|:------------|
| Zakres   |Mały|
|Wersja|4.5|
|Typ|Środowisko uruchomieniowe

#### <a name="affected-apis"></a>Dotyczy interfejsów API

-<xref:System.Printing.PrintSystemJobInfo.JobStream?displayProperty=nameWithType></li></ul>|
