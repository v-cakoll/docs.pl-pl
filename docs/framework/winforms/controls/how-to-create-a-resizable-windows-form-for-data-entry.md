---
title: 'Porady: tworzenie formularza systemu Windows o zmiennych rozmiarach do wpisywania danych'
ms.date: 03/30/2017
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
ms.openlocfilehash: aeab1b506b9ded4c3c2ab527f07a8655a44cad2b
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/16/2019
ms.locfileid: "72396028"
---
# <a name="how-to-create-a-resizable-windows-form-for-data-entry"></a>Porady: tworzenie formularza systemu Windows o zmiennych rozmiarach do wpisywania danych
Dobry układ reaguje na zmiany w wymiarach jego formularza nadrzędnego. Za pomocą kontrolki <xref:System.Windows.Forms.TableLayoutPanel> można rozmieścić układ formularza w celu zmiany rozmiaru i położenia kontrolek w spójny sposób. Formant <xref:System.Windows.Forms.TableLayoutPanel> jest również przydatny, gdy zmiany w zawartości formantów powodują zmiany w układzie. Proces objęty tą procedurą można wykonać w środowisku programu Visual Studio.  Zobacz też [Przewodnik: Tworzenie formularza systemu Windows o zmiennym rozmiarze do wprowadzania danych](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/991eahec(v=vs.100)).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład ilustruje sposób używania kontrolki <xref:System.Windows.Forms.TableLayoutPanel> do kompilowania układu, który reaguje, gdy użytkownik zmienia rozmiar formularza. Przedstawiono w nim również układ, który reaguje na lokalizację.  
  
 [!code-cpp[System.Windows.Forms.TableLayoutPanel.DataEntryForm#1](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.TableLayoutPanel.DataEntryForm/cpp/basicdataentryform.cpp#1)]
 [!code-csharp[System.Windows.Forms.TableLayoutPanel.DataEntryForm#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.TableLayoutPanel.DataEntryForm/CS/basicdataentryform.cs#1)]
 [!code-vb[System.Windows.Forms.TableLayoutPanel.DataEntryForm#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.TableLayoutPanel.DataEntryForm/VB/basicdataentryform.vb#1)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Ten przykład wymaga:  
  
- Odwołania do zestawów system, system. Data, system. Drawing i system. Windows. Forms.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.FlowLayoutPanel>
- <xref:System.Windows.Forms.TableLayoutPanel>
- [Instrukcje: zakotwiczenie i dokowanie kontrolek podrzędnych w kontrolce TableLayoutPanel](how-to-anchor-and-dock-child-controls-in-a-tablelayoutpanel-control.md)
- [Instrukcje: projektowanie układu formularzy Windows Forms dobrze reagującego na lokalizację](how-to-design-a-windows-forms-layout-that-responds-well-to-localization.md)
