---
ms.openlocfilehash: 84f570cbbd97be79426e117d4c97ec182a397fd4
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "66379597"
---
### <a name="ipad-should-not-be-used-in-custom-capabilities-file-because-it-is-now-a-browser-capability"></a>IPad nie należy używać w pliku niestandardowego możliwości, ponieważ jest on obecnie możliwości przeglądarki

|   |   |
|---|---|
|Szczegóły|Począwszy od programu .NET Framework 4.5, iPad jest identyfikatora w pliku możliwości uzyskiwania informacji na temat przeglądarki ASP.NET domyślne z więc nie powinien on używany w pliku niestandardowego możliwości|
|Sugestia|Jeżeli wymagane są funkcje właściwe dla tabletu iPad, należy zmodyfikować zachowanie dla urządzenia iPad, ustawiając możliwości na refID wstępnie zdefiniowanych bram &quot;IPad&quot; zamiast, generując nowy &quot;IPad&quot; identyfikator według agenta użytkownika dopasowanie.|
|Scope|Krawędź|
|Wersja|4.5|
|Typ|Środowisko uruchomieniowe|
