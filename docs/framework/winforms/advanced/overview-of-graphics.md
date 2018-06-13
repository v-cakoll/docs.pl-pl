---
title: Omówienie grafik
ms.date: 03/30/2017
helpviewer_keywords:
- graphics [Windows Forms], using managed interface
- graphics [Windows Forms], about graphics
ms.assetid: a602aef8-a8c8-4c36-9816-74e7bad96a68
ms.openlocfilehash: a69bfc2e9983484f90b1b65abd234df2519b503e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33523556"
---
# <a name="overview-of-graphics"></a>Omówienie grafik
[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] to interfejs programowania aplikacji (API), który wchodzi w skład podsystemu systemu operacyjnego Microsoft Windows. [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] odpowiada za wyświetlanie informacji na ekranach i drukarek. Zgodnie z sugestią, jego nazwa, [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] zastępuje [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)], graficzny interfejs urządzenia dołączone do wcześniejszych wersji systemu Windows.  
  
## <a name="managed-class-interface"></a>Zarządzanej klasy interfejsu  
 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] Interfejsu API jest za pośrednictwem zestaw klas wdrożony jako kodu zarządzanego. Ten zestaw klas jest nazywany *zarządzanej klasy interfejsu* do [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]. Następujące obszary nazw tworzą interfejsu zarządzanej klasy:  
  
-   <xref:System.Drawing>  
  
-   <xref:System.Drawing.Drawing2D>  
  
-   <xref:System.Drawing.Imaging>  
  
-   <xref:System.Drawing.Text>  
  
-   <xref:System.Drawing.Printing>  
  
 Z graficzny interfejs urządzenia takie jak [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)], można wyświetlić informacje dotyczące ekranu lub drukarki, bez konieczności trzeba się troszczyć o szczegóły określony ekran urządzenia. Programistę wykonywania wywołań do metod dostarczonych przez [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] klasy. Tych metod z kolei wywołań odpowiednie do określone sterowniki urządzeń. [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] powoduje aplikacji od sprzętu grafiki. Jest izolacja umożliwiającą programisty do tworzenia aplikacji niezależnych od urządzenia.  
  
## <a name="see-also"></a>Zobacz też  
 [Grafika — omówienie](../../../../docs/framework/winforms/advanced/graphics-overview-windows-forms.md)
