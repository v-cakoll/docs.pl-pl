---
title: FontDialog, składnik — omówienie
ms.date: 03/30/2017
f1_keywords:
- FontDialog
helpviewer_keywords:
- Font dialog box [Windows Forms], Windows Forms
- Font dialog box
- FontDialog component [Windows Forms], about FontDialog component
ms.assetid: daf46e57-1b4b-4b7a-bad0-b50ca7ba75dc
ms.openlocfilehash: 664b756dc068ca283e4f43edbdd0f3266f5d1142
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76745707"
---
# <a name="fontdialog-component-overview-windows-forms"></a>FontDialog — Informacje o składniku (Formularze systemu Windows)
Składnik <xref:System.Windows.Forms.FontDialog> Windows Forms jest wstępnie skonfigurowanym oknem dialogowym, które jest oknem dialogowym standardowe **czcionki** systemu Windows, które służy do udostępnienia czcionek aktualnie zainstalowanych w systemie. Użyj go w aplikacji opartej na systemie Windows jako proste rozwiązanie do wyboru czcionki zamiast konfigurowania własnego okna dialogowego.  
  
 Domyślnie okno dialogowe zawiera pola listy dla czcionki, stylu i rozmiaru czcionki; pola wyboru dla efektów takich jak przekreolenie i podkreolenie; Lista rozwijana dla skryptu; i przykład sposobu wyświetlania czcionki. (Skrypt odnosi się do różnych skryptów znaków, które są dostępne dla danej czcionki, na przykład hebrajski lub japoński). Aby wyświetlić okno dialogowe Czcionka, wywołaj metodę <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A>.  
  
## <a name="key-properties"></a>Właściwości klucza  
 Składnik ma wiele właściwości, które konfigurują jego wygląd. Właściwości ustawiające wybory okna dialogowego są <xref:System.Windows.Forms.FontDialog.Font%2A> i <xref:System.Windows.Forms.FontDialog.Color%2A>. Właściwość <xref:System.Windows.Forms.FontDialog.Font%2A> ustawia czcionkę, styl, rozmiar, skrypt i efekty; na przykład `Arial, 10pt, style=Italic, Strikeout`.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.FontDialog>
- [FontDialog, składnik](fontdialog-component-windows-forms.md)
