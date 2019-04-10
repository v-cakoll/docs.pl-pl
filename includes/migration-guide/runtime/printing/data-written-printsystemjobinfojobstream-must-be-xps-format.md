---
ms.openlocfilehash: 74f00821f2304664729faa8de2f0163c6611f513
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59235641"
---
### <a name="data-written-to-printsystemjobinfojobstream-must-be-in-xps-format"></a>Dane zapisane PrintSystemJobInfo.JobStream musi być w formacie XPS

|   |   |
|---|---|
|Szczegóły|<xref:System.Printing.PrintSystemJobInfo.JobStream> Właściwość udostępnia strumienia zadania drukowania. Użytkownik może wysyłać nieprzetworzone dane do drukowania komponentów systemu operacyjnego, pisząc do tego strumienia. Począwszy od programu .NET Framework 4.5 w systemie Windows 8 i nowszych wersjach systemu operacyjnego Windows, w tym strumieniu dane muszą być w formacie XPS jako strumień pakietu.|
|Sugestia|W danych wyjściowych wydrukowanie zawartości, wykonaj jedną z następujących czynności:<ul><li>Użyj <xref:System.Windows.Xps.XpsDocumentWriter> klasy do wypełniania wyjściowego wydrukowanie zawartości. To jest zalecaną alternatywą.</li><li>Upewnij się, że dane wysyłane do Strumień zwrócony przez <xref:System.Printing.PrintSystemJobInfo.JobStream> właściwość jest w formacie XPS jako strumień pakietu.</li></ul>|
|Zakres|Mały|
|Wersja|4.5|
|Typ|Środowisko uruchomieniowe|
|Dotyczy interfejsów API|<ul><li><xref:System.Printing.PrintSystemJobInfo.JobStream?displayProperty=nameWithType></li></ul>|
