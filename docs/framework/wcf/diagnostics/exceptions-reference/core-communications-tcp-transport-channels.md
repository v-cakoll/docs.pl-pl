---
title: "Komunikacja podstawowa: kanały transportu TCP"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d5cd057f-faec-4e21-ae0e-18bbc22bcfb1
caps.latest.revision: "5"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 92147e3887f9f82e37a4870ec6de767868c97c1b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="core-communications-tcp-transport-channels"></a>Komunikacja podstawowa: kanały transportu TCP
W tym temacie wymieniono wszystkie wyjątki generowane przez kanały transportu TCP.  
  
## <a name="exception-list"></a>Listy wyjątków  
  
|Kod zasobu|Ciąg zasobu|  
|-------------------|---------------------|  
|SocketCloseReadTimeout|Zdalny punkt końcowy określony gniazda nie odpowiada na żądanie zamknięcia w ciągu przydzielonego limitu czasu określonego. Istnieje możliwość, że zdalny punkt końcowy jest nie wywołuje metody Close po odebraniu sygnału EOF (zero) przez operację odbierania. Czas przydzielony na tę operację mógł stanowi część większego limitu czasu.|
