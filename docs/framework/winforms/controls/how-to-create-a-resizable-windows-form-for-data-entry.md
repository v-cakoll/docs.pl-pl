---
title: 'Porady: tworzenie formularza systemu Windows o zmiennych rozmiarach do wpisywania danych'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- TableLayoutPanel control [Windows Forms]
- layout [Windows Forms], resizing
- forms [Windows Forms], creating resizable
- Windows Forms, resizable
ms.assetid: babdf198-404c-485d-a914-ed370c6ecd99
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: d81f47d0a8ba48d18eaf2973d5810672a9aba1b0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-a-resizable-windows-form-for-data-entry"></a>Porady: tworzenie formularza systemu Windows o zmiennych rozmiarach do wpisywania danych
Dobrym układu odpowiada również zmiany w wymiarach jego formularza nadrzędnego. Można użyć <xref:System.Windows.Forms.TableLayoutPanel> formant układu formularza do zmiany rozmiaru i umieść formanty w spójny sposób, jak zmiany wymiarów formularza. <xref:System.Windows.Forms.TableLayoutPanel> Formant jest również przydatne w przypadku gdy zmienia się zawartość formantów Przyczyna zmiany w układzie. Proces omówione w tej procedurze można zrobić w środowisku Visual Studio.  Zobacz też [wskazówki: Tworzenie formularza systemu Windows o zmiennych rozmiarach do wpisywania danych](http://msdn.microsoft.com/library/991eahec\(v=vs.110\)).  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano sposób użycia <xref:System.Windows.Forms.TableLayoutPanel> formantu do tworzenia układu, który reaguje także, gdy użytkownik zmienia rozmiar formularza. Ilustruje też dobrze reagującego na układ.  
  
 [!code-cpp[System.Windows.Forms.TableLayoutPanel.DataEntryForm#1](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.TableLayoutPanel.DataEntryForm/cpp/basicdataentryform.cpp#1)]
 [!code-csharp[System.Windows.Forms.TableLayoutPanel.DataEntryForm#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.TableLayoutPanel.DataEntryForm/CS/basicdataentryform.cs#1)]
 [!code-vb[System.Windows.Forms.TableLayoutPanel.DataEntryForm#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.TableLayoutPanel.DataEntryForm/VB/basicdataentryform.vb#1)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Ten przykład wymaga:  
  
-   Odwołania do zestawów systemu, dane systemowe, System.Drawing i System.Windows.Forms.  
  
 Informacji dotyczących tworzenia tego przykładu z wiersza polecenia dla [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] lub [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)], zobacz [tworzenie z wiersza polecenia](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) lub [kompilowania z wiersza polecenia csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md). Można także utworzyć tym przykładzie [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] przez wklejenie kodu do nowego projektu.  Zobacz też [porady: kompilowanie i uruchamianie pełną Windows formularze kodu przykład za pomocą programu Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Forms.FlowLayoutPanel>  
 <xref:System.Windows.Forms.TableLayoutPanel>  
 [Instrukcje: zakotwiczenie i dokowanie kontrolek podrzędnych w kontrolce TableLayoutPanel](../../../../docs/framework/winforms/controls/how-to-anchor-and-dock-child-controls-in-a-tablelayoutpanel-control.md)  
 [Instrukcje: projektowanie układu formularzy Windows Forms dobrze reagującego na lokalizację](../../../../docs/framework/winforms/controls/how-to-design-a-windows-forms-layout-that-responds-well-to-localization.md)  
 [Środowisko użytkownika systemu Windows firmy Microsoft, oficjalnego wskazówki dla deweloperów interfejsu użytkownika i projektantów. Redmond, WA: Microsoft Press, 1999. (USBN: 0-7356-0566-1)](http://www.microsoft.com/mspress/southpacific/books/book11588.htm)
