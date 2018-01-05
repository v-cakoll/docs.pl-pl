---
title: 'Porady: kopiowanie i wklejanie formantu ElementHost w czasie projektowania'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Windows Forms, content copying and pasting
- interoperability [WPF]
- ElementHost control [Windows Forms], copying and pasting at design time
- WPF user control [Windows Forms], hosting in Windows Forms
ms.assetid: e570375d-2a68-44ba-b4f7-c781af2d20e8
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ffe7d050de84eba8c7962a62a8604a72f78bc2bc
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-copy-and-paste-an-elementhost-control-at-design-time"></a>Porady: kopiowanie i wklejanie formantu ElementHost w czasie projektowania
Ta procedura przedstawia sposób kopiowania formantu Windows Presentation Foundation (WPF) na formularzu systemu Windows.  
  
> [!NOTE]
>  Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania. Aby zmienić ustawienia, wybierz **Import i eksport ustawień** na **narzędzia** menu. Aby uzyskać więcej informacji, zobacz [Dostosowywanie ustawień środowiska w programie Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-copy-and-paste-an-elementhost-control-at-design-time"></a>Kopiowanie i wklejanie formantu ElementHost w czasie projektowania  
  
1.  Dodaj nowy WPF <xref:System.Windows.Controls.UserControl> do projektu formularzy systemu Windows. Użyj domyślnej nazwy dla typu formantu `UserControl1.xaml`. Aby uzyskać więcej informacji, zobacz [wskazówki: Tworzenie nowego WPF zawartości w formularzach systemu Windows w czasie projektowania](../../../../docs/framework/winforms/advanced/walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md).  
  
2.  W **właściwości** okna, ustaw wartość <xref:System.Windows.FrameworkElement.Width%2A> i <xref:System.Windows.FrameworkElement.Height%2A> właściwości `UserControl1` do `200`.  
  
3.  Ustaw wartość <xref:System.Windows.Controls.Control.Background%2A> właściwości `Blue`.  
  
4.  Skompiluj projekt.  
  
5.  Otwórz `Form1` w narzędziu Projektant dla formularzy systemu Windows.  
  
6.  Z **przybornika**, przeciągnij wystąpienia `UserControl1` na formularzu.  
  
     Wystąpienie `UserControl1` znajduje się w nowym <xref:System.Windows.Forms.Integration.ElementHost> formantu o nazwie `elementHost1`.  
  
7.  Z `elementHost1` zaznaczone, naciśnij klawisze CTRL + C, aby skopiować go do Schowka.  
  
8.  Naciśnij klawisze CTRL + V Aby wkleić skopiowanych kontrolki na formularzu.  
  
     Nowy <xref:System.Windows.Forms.Integration.ElementHost> formantu o nazwie `elementHost2` jest tworzony w formularzu.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Forms.Integration.ElementHost>  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>  
 [Przewodnik: kopiowanie i wklejanie kontrolki ElementHost w oddzielnych formularzach Windows Forms](../../../../docs/framework/winforms/advanced/copy--paste-an-elementhost-control-into-forms.md)  
 [Migracja i współdziałanie](../../../../docs/framework/wpf/advanced/migration-and-interoperability.md)  
 [Korzystanie z kontrolek WPF](../../../../docs/framework/winforms/advanced/using-wpf-controls.md)  
 [Projektant WPF](http://msdn.microsoft.com/en-us/c6c65214-8411-4e16-b254-163ed4099c26)
