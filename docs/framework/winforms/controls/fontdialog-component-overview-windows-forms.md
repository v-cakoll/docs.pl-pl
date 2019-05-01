---
title: FontDialog — Informacje o składniku (Formularze systemu Windows)
ms.date: 03/30/2017
f1_keywords:
- FontDialog
helpviewer_keywords:
- Font dialog box [Windows Forms], Windows Forms
- Font dialog box
- FontDialog component [Windows Forms], about FontDialog component
ms.assetid: daf46e57-1b4b-4b7a-bad0-b50ca7ba75dc
ms.openlocfilehash: 7f140807bf4b42e530302190042e729c59248e7f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61789314"
---
# <a name="fontdialog-component-overview-windows-forms"></a>FontDialog — Informacje o składniku (Formularze systemu Windows)
Formularze Windows <xref:System.Windows.Forms.FontDialog> składnik to wstępnie skonfigurowane okno dialogowe, które jest standardowa Windows **czcionki** okno dialogowe, używany do udostępnienia czcionek, które są aktualnie zainstalowane w systemie. Użycie go w aplikacji opartych na Windows proste rozwiązanie dla wybór czcionki audytów Konfigurowanie własnego okno dialogowe.  
  
 Domyślnie okno dialogowe zawiera pola listy czcionki, styl czcionki i rozmiar. pola wyboru dla efektów, jak przekreślenie i podkreślenie; listy rozwijanej, aby skrypt; i przykładowy wygląd czcionki. (Skryptu lub odwołuje się do skryptów inny znak, które są dostępne dla danej czcionki, na przykład, hebrajski japoński.) Aby wyświetlić okno dialogowe czcionki, należy wywołać <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> metody.  
  
## <a name="key-properties"></a>Właściwości klucza  
 Składnik ma wiele właściwości, które skonfigurować jego wygląd. Ustaw opcje Okno dialogowe właściwości są <xref:System.Windows.Forms.FontDialog.Font%2A> i <xref:System.Windows.Forms.FontDialog.Color%2A>. <xref:System.Windows.Forms.FontDialog.Font%2A> Właściwość ustawia czcionkę, style, rozmiar, skrypt i efektów; na przykład `Arial, 10pt, style=Italic, Strikeout`.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.FontDialog>
- [FontDialog, składnik](fontdialog-component-windows-forms.md)
