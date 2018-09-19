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
ms.openlocfilehash: 3c821177ca897e617885425217ac0b6659b5ea6e
ms.sourcegitcommit: 5bbfe34a9a14e4ccb22367e57b57585c208cf757
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46003454"
---
# <a name="securing-state-data"></a>Zabezpieczanie danych o stanie
Aplikacje, które obsługują dane poufne lub wprowadzić dowolnego rodzaju decyzje dotyczące bezpieczeństwa należy zachować te dane w ich własnych kontrolą i nie może dopuścić do innego potencjalnie złośliwego kodu bezpośrednio dostępu do danych. Najlepszym sposobem, aby chronić dane w pamięci jest do deklarowania dane jako prywatny lub wewnętrzny (z zakresu ograniczone do tego samego zestawu) zmienne. Jednak nawet w tych danych podlega dostępu, których należy wiedzieć:  
  
-   Za pomocą mechanizmów odbicia, wysoce zaufanym kodem, który może odwoływać się do obiektu może pobierać i ustawiać prywatnych elementów członkowskich.  
  
-   Za pomocą serializacji, wysoce zaufanym kodem może efektywnie pobierać i ustawiać prywatne składowe jeśli mogą uzyskać dostępu do odpowiednich danych w postaci serializowanej obiektu.  
  
-   W obszarze debugowania, te dane mogą być odczytywane.  
  
 Upewnij się, brak swoje własne metody lub właściwości przypadkowo udostępnia te wartości.  
  
## <a name="see-also"></a>Zobacz także

- [Wytyczne dotyczące bezpiecznego programowania](../../../docs/standard/security/secure-coding-guidelines.md)
