---
title: Konwertowanie typów programu .NET Framework na ciągi
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: dc2e2b65-f623-4dc3-938b-d2a054d6832c
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 98ebc9248b0585295adf12e04dece0fef654c2e8
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61953988"
---
# <a name="converting-net-framework-types-to-strings"></a>Konwertowanie typów programu .NET Framework na ciągi
Jeśli chcesz przekonwertować typ .NET Framework na ciąg, użyj **ToString** metody. **ToString** metoda zwraca reprezentację ciągu przekazany typ to. Poniższa tabela zawiera listę typów programu .NET Framework, które zwracają ciąg w formacie, który jest mapowany do specyfikacji schematu XML (XSD).  
  
|Typ programu .NET Framework|Ciąg typ zwracany|  
|-------------------------|--------------------------|  
|Boolean|"true", "false"|  
|Single.PositiveInfinity|"INF"|  
|Single.NegativeInfinity|"-INF"|  
|Double.PositiveInfinity|"INF"|  
|Double.NegativeInfinity|"-INF"|  
|DataGodzina|Format to RRRR-MM-ddTHH:mm:sszzzzzz i jego podzbiory.|  
|Przedział czasu|Format jest PnYnMnTnHnMnS, na przykład `P2Y10M15DT10H30M20S` jest wartość typu duration 10hours 2 lata, 10 miesięcy, 15 dni, 30 minut i 20 sekund.|  
  
## <a name="see-also"></a>Zobacz także

- [Konwersja typów danych XML](../../../../docs/standard/data/xml/conversion-of-xml-data-types.md)
- [Konwertowanie ciągów na typy danych programu .NET Framework](../../../../docs/standard/data/xml/converting-strings-to-dotnet-data-types.md)
