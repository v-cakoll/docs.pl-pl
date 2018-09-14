---
title: Konwertowanie typów programu .NET Framework na ciągi znaków
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: dc2e2b65-f623-4dc3-938b-d2a054d6832c
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 59e288a756a022763bae2235964a8b25a9d72bd1
ms.sourcegitcommit: 76a304c79a32aa13889ebcf4b9789a4542b48e3e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/13/2018
ms.locfileid: "45525865"
---
# <a name="converting-net-framework-types-to-strings"></a>Konwertowanie typów programu .NET Framework na ciągi znaków
Jeśli chcesz przekonwertować typ .NET Framework na ciąg, użyj **ToString** metody. **ToString** metoda zwraca reprezentację ciągu przekazany typ to. Poniższa tabela zawiera listę typów programu .NET Framework, które zwracają ciąg w formacie, który jest mapowany do specyfikacji schematu XML (XSD).  
  
|Typ programu .NET Framework|Ciąg typ zwracany|  
|-------------------------|--------------------------|  
|Boolean|"true", "fałsz"|  
|Single.PositiveInfinity|"INF"|  
|Single.NegativeInfinity|"-INF"|  
|Double.PositiveInfinity|"INF"|  
|Double.NegativeInfinity|"-INF"|  
|DataGodzina|Format to RRRR-MM-ddTHH:mm:sszzzzzz i jego podzbiory.|  
|Przedział czasu|Format jest PnYnMnTnHnMnS, na przykład `P2Y10M15DT10H30M20S` jest wartość typu duration 10hours 2 lata, 10 miesięcy, 15 dni, 30 minut i 20 sekund.|  
  
## <a name="see-also"></a>Zobacz także

- [Konwersja typów danych XML](../../../../docs/standard/data/xml/conversion-of-xml-data-types.md)  
- [Konwertowanie ciągów na typy danych programu .NET Framework](../../../../docs/standard/data/xml/converting-strings-to-dotnet-data-types.md)
