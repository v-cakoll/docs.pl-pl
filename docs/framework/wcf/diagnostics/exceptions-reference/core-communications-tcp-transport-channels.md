---
title: 'Komunikacja podstawowa: kanały transportu TCP'
ms.date: 03/30/2017
ms.assetid: d5cd057f-faec-4e21-ae0e-18bbc22bcfb1
ms.openlocfilehash: 0dfbf939b39d53f104d749e0c0d24e04a05185e5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33473110"
---
# <a name="core-communications-tcp-transport-channels"></a>Komunikacja podstawowa: kanały transportu TCP
W tym temacie wymieniono wszystkie wyjątki generowane przez kanały transportu TCP.  
  
## <a name="exception-list"></a>Listy wyjątków  
  
|Kod zasobu|Ciąg zasobu|  
|-------------------|---------------------|  
|SocketCloseReadTimeout|Zdalny punkt końcowy określony gniazda nie odpowiada na żądanie zamknięcia w ciągu przydzielonego limitu czasu określonego. Istnieje możliwość, że zdalny punkt końcowy jest nie wywołuje metody Close po odebraniu sygnału EOF (zero) przez operację odbierania. Czas przydzielony na tę operację mógł stanowi część większego limitu czasu.|
