---
title: Omówienie grafik
ms.date: 03/30/2017
helpviewer_keywords:
- graphics [Windows Forms], using managed interface
- graphics [Windows Forms], about graphics
ms.assetid: a602aef8-a8c8-4c36-9816-74e7bad96a68
ms.openlocfilehash: f0e2fd9dcf31e5fdce16b5a3b6fd21eab6eab66a
ms.sourcegitcommit: b1cfd260928d464d91e20121f9bdba7611c94d71
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/02/2019
ms.locfileid: "67505322"
---
# <a name="overview-of-graphics"></a>Omówienie grafik
GDI + jest interfejs programowania aplikacji (API), który wchodzi w skład podsystemu systemu operacyjnego Microsoft Windows. GDI + jest odpowiedzialny za wyświetlanie informacji na ekranach i drukarki. Jak sugeruje nazwa, GDI + jest następcą programu interfejsu GDI, graficzny interfejs urządzenia dołączone do wcześniejszych wersji systemu Windows.  
  
## <a name="managed-class-interface"></a>Interfejs klasy zarządzanej  
 Interfejs API GDI + jest udostępniany za pośrednictwem zestaw klas wdrożone jako kod zarządzany. Ten zestaw klas jest nazywany *interfejsu klasy zarządzanej* do interfejsu GDI +. Następujące przestrzenie nazw tworzą interfejs zarządzanej klasy:  
  
- <xref:System.Drawing>  
  
- <xref:System.Drawing.Drawing2D>  
  
- <xref:System.Drawing.Imaging>  
  
- <xref:System.Drawing.Text>  
  
- <xref:System.Drawing.Printing>  
  
 Za pomocą graficzny interfejs urządzenia, takich jak interfejs GDI + można wyświetlić informacje na ekranie lub drukarki, bez konieczności liczyć się szczegółowe informacje o urządzeniu określonej. Programistę wykonywania wywołań do metod dostarczonych przez klasy interfejsu GDI +. Tych metod należy z kolei odpowiednie wywołania określone sterowniki urządzeń. GDI + powoduje, że aplikacja od sprzętu graficznego. Jest to izolacji, umożliwiająca z programistą podczas tworzenia aplikacji niezależnych od urządzenia.  
  
## <a name="see-also"></a>Zobacz także

- [Grafika — omówienie](graphics-overview-windows-forms.md)
