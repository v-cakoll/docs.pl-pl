---
title: "Używanie kontenerów grafiki"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- graphics [Windows Forms], using containers
- graphics containers
- examples [Windows Forms], graphics containers
ms.assetid: 74632f91-cefa-4f51-ab7c-f9ac91942caf
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 337057e10e03712aa93b00d9c687374e53f8dd03
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2017
---
# <a name="using-graphics-containers"></a>Używanie kontenerów grafiki
A <xref:System.Drawing.Graphics> obiekt zapewnia metody <xref:System.Drawing.Graphics.DrawLine%2A>, <xref:System.Drawing.Graphics.DrawImage%2A>, i <xref:System.Drawing.Graphics.DrawString%2A> do wyświetlania obrazów wektora, obrazy rastrowe i tekstu. A <xref:System.Drawing.Graphics> obiekt ma również kilka właściwości wpływające na jakości i orientację elementów, które są rysowane. Na przykład właściwość tryb wygładzania Określa, czy zastosowano antyaliasingu do linii i krzywych i właściwości transformacji świata wpływa na pozycji i obracania elementów, które są rysowane.  
  
 A <xref:System.Drawing.Graphics> obiekt jest skojarzony z urządzeniem określony ekran. Jeśli używasz <xref:System.Drawing.Graphics> obiektu do rysowania w oknie <xref:System.Drawing.Graphics> obiektu jest także powiązany z tym poszczególnego okna.  
  
 A <xref:System.Drawing.Graphics> obiektu można traktować jako kontener ponieważ posiada zbiór właściwości, które wpływają na rysunku i jest on połączony informacje specyficzne dla danego urządzenia. Możesz utworzyć kontener dodatkowej w ramach istniejącej <xref:System.Drawing.Graphics> obiektu przez wywołanie metody <xref:System.Drawing.Graphics.BeginContainer%2A> metoda tego <xref:System.Drawing.Graphics> obiektu.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Zarządzaniu stanem obiektu graficznego](../../../../docs/framework/winforms/advanced/managing-the-state-of-a-graphics-object.md)  
 W tym artykule opisano sposób zarządzania ustawieniami jakości, obszar przycinania i transformacje <xref:System.Drawing.Graphics> obiektu.  
  
 [Używanie zagnieżdżonych kontenerów grafiki](../../../../docs/framework/winforms/advanced/using-nested-graphics-containers.md)  
 Przedstawia sposób użycia kontenerów do sterowania stanem <xref:System.Drawing.Graphics> obiektu.
