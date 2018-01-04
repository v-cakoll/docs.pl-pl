---
title: "Wyjątki hostingu"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ad9e14f8-fa17-4d59-b365-fe0e7ec17c98
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b296578efb6eb9b1e6372dbad647fdea22dbaddf
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="hosting-exceptions"></a>Wyjątki hostingu
W tym temacie wymieniono wszystkie wyjątki generowane przez hostingu.  
  
## <a name="exception-list"></a>Listy wyjątków  
  
|Kod zasobu|Ciąg zasobu|  
|-------------------|---------------------|  
|Hosting_AddressIsAbsoluteUri|Pełny identyfikator URI nie jest dozwolone. Pełne identyfikatory URI są niedozwolone dla interfejsu API ServiceHostingEnvironment.EnsureServiceAvailable. Za pomocą ścieżki wirtualnej do odpowiedniej usługi.|  
|Hosting_BuildProviderCouldNotCreateType|Nie można załadować określonego typu CLR podczas kompilacji usługi. Sprawdź, czy ten typ albo jest zdefiniowany w pliku źródłowym znajduje się w aplikacji \\katalogu \App_Code, zawarty w skompilowanym zestawie znajduje się w aplikacji \\\bin katalogu lub w zestawie zainstalowanym w Globalna pamięć podręczna zestawów. Nazwa typu jest rozróżniana wielkość liter. Katalogi, takich jak \\\App_Code i \\\bin musi znajdować się w katalogu głównym aplikacji. \\\App_Code i \\\bin katalogów nie mogą być zagnieżdżone w podkatalogach.|
