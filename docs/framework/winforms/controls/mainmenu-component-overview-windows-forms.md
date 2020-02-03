---
title: MainMenu — Informacje o składniku
ms.date: 03/30/2017
f1_keywords:
- MenuItem
- MainMenu
helpviewer_keywords:
- MainMenu control [Windows Forms], about MainMenu control
- menus
ms.assetid: b41cc5a3-cc59-4996-aa3c-8dd9c17d3c90
ms.openlocfilehash: 8bc35de239429214d6b493b343d1dd6c898f4d37
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76745114"
---
# <a name="mainmenu-component-overview-windows-forms"></a>MainMenu — Informacje o składniku (Formularze systemu Windows)
> [!IMPORTANT]
> Mimo że <xref:System.Windows.Forms.MenuStrip> i <xref:System.Windows.Forms.ContextMenuStrip> Zastąp i Dodaj funkcje do <xref:System.Windows.Forms.MainMenu> i <xref:System.Windows.Forms.ContextMenu> kontroli nad poprzednimi wersjami, <xref:System.Windows.Forms.MainMenu> i <xref:System.Windows.Forms.ContextMenu> są zachowywane w celu zapewnienia zgodności z poprzednimi wersjami i w przyszłości w przypadku wybrania tej opcji.  
  
 Składnik <xref:System.Windows.Forms.MainMenu> Windows Forms wyświetla menu w czasie wykonywania. Wszystkie podmenu menu głównego i poszczególnych elementów są <xref:System.Windows.Forms.MenuItem> obiektów.  
  
## <a name="key-properties"></a>Właściwości klucza  
 Element menu można wyznaczyć jako element domyślny, ustawiając właściwość <xref:System.Windows.Forms.MenuItem.DefaultItem%2A> na `true`. Element domyślny jest wyświetlany pogrubiony tekst po kliknięciu menu. Właściwość <xref:System.Windows.Forms.MenuItem.Checked%2A> elementu menu jest `true` lub `false`i wskazuje, czy element menu jest zaznaczony. Właściwość <xref:System.Windows.Forms.MenuItem.RadioCheck%2A> elementu menu dostosowuje wygląd zaznaczonego elementu: Jeśli <xref:System.Windows.Forms.MenuItem.RadioCheck%2A> jest ustawiona na `true`, obok elementu zostanie wyświetlony przycisk radiowy. Jeśli <xref:System.Windows.Forms.MenuItem.RadioCheck%2A> jest ustawiona na `false`, obok elementu pojawia się znacznik wyboru.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.MainMenu>
- <xref:System.Windows.Forms.Menu>
- <xref:System.Windows.Forms.MenuItem>
- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ContextMenuStrip>
- [MenuStrip, kontrolka — omówienie](menustrip-control-overview-windows-forms.md)
