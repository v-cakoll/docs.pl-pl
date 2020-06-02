---
title: Konwertowanie typów programu .NET Framework na ciągi
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: dc2e2b65-f623-4dc3-938b-d2a054d6832c
ms.openlocfilehash: d232fb0e3ea4cf3189294d6e6f43ae9270417407
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2020
ms.locfileid: "84287821"
---
# <a name="converting-net-framework-types-to-strings"></a>Konwertowanie typów programu .NET Framework na ciągi
Jeśli chcesz skonwertować typ .NET Framework na ciąg, użyj metody **ToString** . Metoda **ToString** zwraca ciąg reprezentujący typ, który został przesłany. Poniższa tabela zawiera listę typów .NET Framework, które zwracają ciąg w formacie, który jest mapowany na specyfikacje schematu XML (XSD).  
  
|Typ programu .NET Framework|Zwrócony typ ciągu|  
|-------------------------|--------------------------|  
|Boolean (wartość logiczna)|"true", "false"|  
|Single. PositiveInfinity|INF|  
|Single. NegativeInfinity|"-INF"|  
|Double. PositiveInfinity|INF|  
|Double. NegativeInfinity|"-INF"|  
|DateTime|Format to RRRR-MM-DDTgg: mm: sszzzzzz i jego podzestawy.|  
|Zakres czasu|Format to PnYnMnTnHnMnS, na przykład, `P2Y10M15DT10H30M20S` wynosi okres 2 lat, 10 miesięcy, 15 dni, 10hours, 30 minut i 20 sekund.|  
  
## <a name="see-also"></a>Zobacz także

- [Konwersja typów danych XML](conversion-of-xml-data-types.md)
- [Konwertowanie ciągów na typy danych programu .NET Framework](converting-strings-to-dotnet-data-types.md)
