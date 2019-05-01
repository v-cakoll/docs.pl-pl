---
title: Wyjątki hostingu
ms.date: 03/30/2017
ms.assetid: ad9e14f8-fa17-4d59-b365-fe0e7ec17c98
ms.openlocfilehash: f2bc7d0ca09faa2598990437295d1abf0cff3c45
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61934735"
---
# <a name="hosting-exceptions"></a>Wyjątki hostingu
Ten temat zawiera listę wszystkich wyjątków generowanych przez hostingu.  
  
## <a name="exception-list"></a>Lista wyjątków  
  
|Kod zasobu|Ciąg zasobu|  
|-------------------|---------------------|  
|Hosting_AddressIsAbsoluteUri|Pełny identyfikator URI nie jest dozwolone. Pełne identyfikatory URI nie są dozwolone w przypadku ServiceHostingEnvironment.EnsureServiceAvailable interfejsu API. Użyj ścieżki wirtualnej dla odpowiedniej usługi.|  
|Hosting_BuildProviderCouldNotCreateType|Nie można załadować określonego typu CLR podczas kompilacji usługi. Sprawdź, czy ten typ, albo jest zdefiniowany w pliku źródłowym, znajduje się w aplikacji \\katalogu \App_Code, zawarty w skompilowanym zestawie znajduje się w aplikacji \\\bin katalogu lub obecny w zestawie zainstalowanym w Globalna pamięć podręczna zestawów. Nazwa typu jest rozróżniana wielkość liter. Katalogi, takich jak \\\App_Code i \\\bin musi znajdować się w katalogu głównym aplikacji. \\\App_Code i \\\bin katalogów nie mogą być zagnieżdżone w podkatalogach.|
