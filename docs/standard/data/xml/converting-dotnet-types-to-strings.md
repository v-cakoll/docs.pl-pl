---
title: Konwertowanie typów programu .NET Framework na ciągi
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: dc2e2b65-f623-4dc3-938b-d2a054d6832c
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b1e9b22a4bc876e9b02ec0da0439682082d2d706
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="converting-net-framework-types-to-strings"></a>Konwertowanie typów programu .NET Framework na ciągi
Aby przekonwertować na ciąg typu .NET Framework, należy użyć **ToString** metody. **ToString** metoda zwraca reprezentację ciągu przekazany typ. Poniższa tabela zawiera listę typów .NET Framework, które zwracają ciąg w formacie, który jest mapowany na specyfikacje schematu XML (XSD).  
  
|Typ programu .NET Framework|String — typ zwracany|  
|-------------------------|--------------------------|  
|Boolean|"true", "fałsz"|  
|Single.PositiveInfinity|"INF"|  
|Single.NegativeInfinity|"-INF"|  
|Double.PositiveInfinity|"INF"|  
|Double.NegativeInfinity|"-INF"|  
|DataGodzina|Format to RRRR-MM-ddTHH:mm:sszzzzzz i jego podzestawy.|  
|Zakres czasu|Format jest PnYnMnTnHnMnS, na przykład `P2Y10M15DT10H30M20S` jest czas trwania 10hours 2 lata, 10 miesięcy, 15 dni, 30 minut i 20 sekund.|  
  
## <a name="see-also"></a>Zobacz też  
 [Konwersja typów danych XML](../../../../docs/standard/data/xml/conversion-of-xml-data-types.md)  
 [Konwertowanie ciągów na typy danych programu .NET Framework](../../../../docs/standard/data/xml/converting-strings-to-dotnet-data-types.md)
