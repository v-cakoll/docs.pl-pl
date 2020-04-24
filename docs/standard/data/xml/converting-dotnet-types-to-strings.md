---
title: Konwertowanie typów programu .NET Framework na ciągi
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: dc2e2b65-f623-4dc3-938b-d2a054d6832c
ms.openlocfilehash: a63e0175f6660967eb4aa678c6731d353e44e2d5
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75711080"
---
# <a name="converting-net-framework-types-to-strings"></a>Konwertowanie typów programu .NET Framework na ciągi
Jeśli chcesz skonwertować typ .NET Framework na ciąg, użyj metody **ToString** . Metoda **ToString** zwraca ciąg reprezentujący typ, który został przesłany. Poniższa tabela zawiera listę typów .NET Framework, które zwracają ciąg w formacie, który jest mapowany na specyfikacje schematu XML (XSD).  
  
|Typ programu .NET Framework|Zwrócony typ ciągu|  
|-------------------------|--------------------------|  
|Wartość logiczna|"true", "false"|  
|Single. PositiveInfinity|INF|  
|Single. NegativeInfinity|"-INF"|  
|Double. PositiveInfinity|INF|  
|Double. NegativeInfinity|"-INF"|  
|DateTime|Format to RRRR-MM-DDTgg: mm: sszzzzzz i jego podzestawy.|  
|Zakres czasu|Format to PnYnMnTnHnMnS, na przykład, `P2Y10M15DT10H30M20S` wynosi okres 2 lat, 10 miesięcy, 15 dni, 10hours, 30 minut i 20 sekund.|  
  
## <a name="see-also"></a>Zobacz też

- [Konwersja typów danych XML](../../../../docs/standard/data/xml/conversion-of-xml-data-types.md)
- [Konwertowanie ciągów na typy danych programu .NET Framework](../../../../docs/standard/data/xml/converting-strings-to-dotnet-data-types.md)
