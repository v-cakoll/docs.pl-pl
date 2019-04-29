---
title: Omówienie grafik
ms.date: 03/30/2017
helpviewer_keywords:
- graphics [Windows Forms], using managed interface
- graphics [Windows Forms], about graphics
ms.assetid: a602aef8-a8c8-4c36-9816-74e7bad96a68
ms.openlocfilehash: a95086645771de61cfc859e34b225992bc16eac9
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61641349"
---
# <a name="overview-of-graphics"></a>Omówienie grafik
[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] to interfejs programowania aplikacji (API), który wchodzi w skład podsystemu systemu operacyjnego Microsoft Windows. [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] odpowiada za wyświetlanie informacji na ekranach i drukarki. Jak sugeruje nazwa, [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] jest następcą programu [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)], graficzny interfejs urządzenia dołączone do wcześniejszych wersji systemu Windows.  
  
## <a name="managed-class-interface"></a>Interfejs klasy zarządzanej  
 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] Interfejs API jest udostępniany za pośrednictwem zestaw klas wdrożone jako kod zarządzany. Ten zestaw klas jest nazywany *interfejsu klasy zarządzanej* do [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]. Następujące przestrzenie nazw tworzą interfejs zarządzanej klasy:  
  
- <xref:System.Drawing>  
  
- <xref:System.Drawing.Drawing2D>  
  
- <xref:System.Drawing.Imaging>  
  
- <xref:System.Drawing.Text>  
  
- <xref:System.Drawing.Printing>  
  
 Za pomocą graficzny interfejs urządzenia takie jak [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)], informacje możesz wyświetlać na ekranie lub drukarki, bez konieczności liczyć się szczegółowe informacje o urządzeniu określony ekran. Programistę wykonywania wywołań do metod dostarczonych przez [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] klasy. Tych metod należy z kolei odpowiednie wywołania określone sterowniki urządzeń. [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] powoduje, że aplikacja od sprzętu graficznego. Jest to izolacji, umożliwiająca z programistą podczas tworzenia aplikacji niezależnych od urządzenia.  
  
## <a name="see-also"></a>Zobacz także

- [Grafika — omówienie](graphics-overview-windows-forms.md)
