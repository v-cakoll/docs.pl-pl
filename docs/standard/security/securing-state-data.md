---
title: Zabezpieczanie danych o stanie
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- security [.NET Framework], state data
- code security, state data
- secure coding, state data
- state data security
ms.assetid: 12671309-2877-43fe-a3df-6863507e712d
author: mairaw
ms.author: mairaw
ms.openlocfilehash: fe941fff7091fb579e41a3c417dbb2129bcf3e8c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33580786"
---
# <a name="securing-state-data"></a>Zabezpieczanie danych o stanie
Aplikacji, które obsługują dane poufne lub wprowadzić dowolny rodzaj decyzje zabezpieczeń muszą zachować te dane pod kontrolą własne i nie może dopuścić do innych potencjalnie niebezpiecznego kodu bezpośrednio uzyskać dostęp do danych. Najlepszym sposobem na potrzeby ochrony danych w pamięci jest deklaruje dane jako prywatny lub wewnętrzny (z zakresem, ograniczone do tego samego zestawu) zmienne. Jednak nawet te dane podlega dostępu, które należy zwrócić uwagę:  
  
-   Za pomocą mechanizmów odbicia, wysoce zaufanych kod, który może odwoływać się do obiektu można get i set prywatne elementy członkowskie.  
  
-   Za pomocą serializacji, wysoce zaufanych kodu można skutecznie get i set prywatne elementy członkowskie Jeśli można uzyskać dostępu do odpowiednich danych w formularzu serializacji obiektu.  
  
-   W obszarze debugowania, mogą być odczytywane dane.  
  
 Upewnij się, że żaden z własnych metody lub właściwości przypadkowo udostępnia te wartości.  
  
## <a name="see-also"></a>Zobacz też  
 [Wytyczne dotyczące bezpiecznego programowania](../../../docs/standard/security/secure-coding-guidelines.md)
