---
title: Zabezpieczanie danych o stanie
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- security [.NET Framework], state data
- code security, state data
- secure coding, state data
- state data security
ms.assetid: 12671309-2877-43fe-a3df-6863507e712d
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: d5f8c4d17e17f7bcdf58db7052dbb2cf2b737a9c
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/23/2017
---
# <a name="securing-state-data"></a>Zabezpieczanie danych o stanie
Aplikacji, które obsługują dane poufne lub wprowadzić dowolny rodzaj decyzje zabezpieczeń muszą zachować te dane pod kontrolą własne i nie może dopuścić do innych potencjalnie niebezpiecznego kodu bezpośrednio uzyskać dostęp do danych. Najlepszym sposobem na potrzeby ochrony danych w pamięci jest deklaruje dane jako prywatny lub wewnętrzny (z zakresem, ograniczone do tego samego zestawu) zmienne. Jednak nawet te dane podlega dostępu, które należy zwrócić uwagę:  
  
-   Za pomocą mechanizmów odbicia, wysoce zaufanych kod, który może odwoływać się do obiektu można get i set prywatne elementy członkowskie.  
  
-   Za pomocą serializacji, wysoce zaufanych kodu można skutecznie get i set prywatne elementy członkowskie Jeśli można uzyskać dostępu do odpowiednich danych w formularzu serializacji obiektu.  
  
-   W obszarze debugowania, mogą być odczytywane dane.  
  
 Upewnij się, że żaden z własnych metody lub właściwości przypadkowo udostępnia te wartości.  
  
## <a name="see-also"></a>Zobacz też  
 [Wytyczne dotyczące bezpiecznego programowania](../../../docs/standard/security/secure-coding-guidelines.md)
