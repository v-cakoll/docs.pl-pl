---
title: "Konwertowanie typów programu .NET Framework na ciągi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: dc2e2b65-f623-4dc3-938b-d2a054d6832c
caps.latest.revision: "3"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 6ca134e13593fdacd759b0000e0e159f76ea067f
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/23/2017
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
