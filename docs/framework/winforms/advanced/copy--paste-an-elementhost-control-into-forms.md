---
title: "Wskazówki: kopiowanie i wklejanie formantu ElementHost w oddzielnych formularzach systemu Windows"
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
ms.assetid: 6e81bb13-577c-46c3-a1cf-8d15969fb83e
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 65882925c6fbe3e9b393b139a937bc9a1f95ed04
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="walkthrough-copying-and-pasting-an-elementhost-control-into-separate-windows-forms"></a>Wskazówki: kopiowanie i wklejanie formantu ElementHost w oddzielnych formularzach systemu Windows
Ten przewodnik przedstawia sposób kopiowania kontrolki Windows Presentation Foundation (WPF) z jednego formularza systemu Windows na inny.  
  
 W tym przewodniku należy wykonać następujące zadania:  
  
-   Tworzenie projektu.  
  
-   Skopiuj kontrolce WPF.  
  
> [!NOTE]
>  Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania. Aby zmienić ustawienia, wybierz **Import i eksport ustawień** na **narzędzia** menu. Aby uzyskać więcej informacji, zobacz [Dostosowywanie ustawień środowiska w programie Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 Następujące składniki są wymagane do przeprowadzenia tego instruktażu:  
  
-   [!INCLUDE[vs_dev11_long](../../../../includes/vs-dev11-long-md.md)].  
  
## <a name="creating-the-project"></a>Tworzenie projektu  
 Pierwszym krokiem jest utworzenie projektu formularzy systemu Windows.  
  
> [!NOTE]
>  Jeżeli hostowanie zawartości WPF, obsługiwane są tylko C# i Visual Basic, projekty.  
  
#### <a name="to-create-the-project"></a>Aby utworzyć projekt  
  
-   Utwórz nowy projekt aplikacji formularzy systemu Windows w języku Visual Basic lub Visual C# o nazwie `CopyElementHost`.  
  
## <a name="copying-a-wpf-control"></a>Kopiowanie kontrolce WPF  
 Po dodaniu formantu WPF do projektu, skopiuj go do innych formularzy w projekcie.  
  
#### <a name="to-copy-a-wpf-control"></a>Aby skopiować kontrolce WPF  
  
1.  Dodaj nowy WPF <xref:System.Windows.Controls.UserControl> projektu do rozwiązania. Użyj domyślnej nazwy dla typu formantu `UserControl1.xaml`. Aby uzyskać więcej informacji, zobacz [wskazówki: Tworzenie nowego WPF zawartości w formularzach systemu Windows w czasie projektowania](../../../../docs/framework/winforms/advanced/walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md).  
  
2.  Skompiluj projekt.  
  
3.  Otwórz `Form1` w narzędziu Projektant dla formularzy systemu Windows.  
  
4.  Z **przybornika**, przeciągnij wystąpienia `UserControl1` na formularzu.  
  
     Wystąpienie `UserControl1` znajduje się w nowym <xref:System.Windows.Forms.Integration.ElementHost> formantu o nazwie `elementHost1`.  
  
5.  Z `elementHost1` zaznaczone, naciśnij klawisze CTRL + C, aby skopiować go do Schowka.  
  
6.  Dodaj nowego formularza systemu Windows do projektu. Użyj domyślnej nazwy dla typu formularza `Form2`.  
  
7.  Z `Form2` Otwórz w narzędziu Projektant dla formularzy systemu Windows, naciśnij klawisze CTRL + V Aby wkleić kopię `elementHost1` na formularzu.  
  
     Formancie skopiowanego nosi również `elementHost1`, ponieważ jest prywatny pole `Form2` klasy. Nie istnieje żadne kolizję nazw z `elementHost1` w `Form1` klasy.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Forms.Integration.ElementHost>  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>  
 [Migracja i współdziałanie](../../../../docs/framework/wpf/advanced/migration-and-interoperability.md)  
 [Korzystanie z formantów WPF](../../../../docs/framework/winforms/advanced/using-wpf-controls.md)  
 [Projektant WPF](http://msdn.microsoft.com/en-us/c6c65214-8411-4e16-b254-163ed4099c26)
