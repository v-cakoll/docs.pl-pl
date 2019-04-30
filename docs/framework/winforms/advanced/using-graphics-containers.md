---
title: Używanie kontenerów grafiki
ms.date: 03/30/2017
helpviewer_keywords:
- graphics [Windows Forms], using containers
- graphics containers
- examples [Windows Forms], graphics containers
ms.assetid: 74632f91-cefa-4f51-ab7c-f9ac91942caf
ms.openlocfilehash: cfad7254057a31ea8268784cd4b6849850f3e2aa
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61766158"
---
# <a name="using-graphics-containers"></a>Używanie kontenerów grafiki
A <xref:System.Drawing.Graphics> obiekt zapewnia metody <xref:System.Drawing.Graphics.DrawLine%2A>, <xref:System.Drawing.Graphics.DrawImage%2A>, i <xref:System.Drawing.Graphics.DrawString%2A> do wyświetlania obrazy wektorowe, rastrowych obrazów i tekstu. A <xref:System.Drawing.Graphics> obiekt ma również kilka właściwości, które mają wpływ na jakość i orientację elementów, które są rysowane. Na przykład właściwość tryb wygładzania Określa, czy dotyczy antyaliasingu do linii i krzywych i właściwości transformacji świata ma wpływ na położenie i obracania elementów, które są rysowane.  
  
 A <xref:System.Drawing.Graphics> obiekt jest skojarzony z urządzeniem określony ekran. Kiedy używasz <xref:System.Drawing.Graphics> obiektu, aby narysować w oknie <xref:System.Drawing.Graphics> obiektu jest również skojarzony z tym konkretnym oknie.  
  
 Element <xref:System.Drawing.Graphics> obiektu można traktować jako kontener, ponieważ posiada zbiór właściwości, które wpływają na rysunku i prowadzi do informacji specyficznych dla urządzenia. Można utworzyć pomocniczego kontener w ramach istniejącego <xref:System.Drawing.Graphics> obiektu przez wywołanie metody <xref:System.Drawing.Graphics.BeginContainer%2A> metodę, która <xref:System.Drawing.Graphics> obiektu.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Zarządzanie stanem obiektu graficznego](managing-the-state-of-a-graphics-object.md)  
 W tym artykule opisano sposób Zarządzanie ustawieniami jakości, obszar przycinania i przekształcanie <xref:System.Drawing.Graphics> obiektu.  
  
 [Używanie zagnieżdżonych kontenerów grafiki](using-nested-graphics-containers.md)  
 Pokazuje, jak używać kontenerów do sterowania stanem <xref:System.Drawing.Graphics> obiektu.
