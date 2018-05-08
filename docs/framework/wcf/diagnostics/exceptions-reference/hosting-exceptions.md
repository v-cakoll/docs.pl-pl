---
title: Wyjątki hostingu
ms.date: 03/30/2017
ms.assetid: ad9e14f8-fa17-4d59-b365-fe0e7ec17c98
ms.openlocfilehash: f2bc7d0ca09faa2598990437295d1abf0cff3c45
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="hosting-exceptions"></a>Wyjątki hostingu
W tym temacie wymieniono wszystkie wyjątki generowane przez hostingu.  
  
## <a name="exception-list"></a>Listy wyjątków  
  
|Kod zasobu|Ciąg zasobu|  
|-------------------|---------------------|  
|Hosting_AddressIsAbsoluteUri|Pełny identyfikator URI nie jest dozwolone. Pełne identyfikatory URI są niedozwolone dla interfejsu API ServiceHostingEnvironment.EnsureServiceAvailable. Za pomocą ścieżki wirtualnej do odpowiedniej usługi.|  
|Hosting_BuildProviderCouldNotCreateType|Nie można załadować określonego typu CLR podczas kompilacji usługi. Sprawdź, czy ten typ albo jest zdefiniowany w pliku źródłowym znajduje się w aplikacji \\katalogu \App_Code, zawarty w skompilowanym zestawie znajduje się w aplikacji \\\bin katalogu lub w zestawie zainstalowanym w Globalna pamięć podręczna zestawów. Nazwa typu jest rozróżniana wielkość liter. Katalogi, takich jak \\\App_Code i \\\bin musi znajdować się w katalogu głównym aplikacji. \\\App_Code i \\\bin katalogów nie mogą być zagnieżdżone w podkatalogach.|
