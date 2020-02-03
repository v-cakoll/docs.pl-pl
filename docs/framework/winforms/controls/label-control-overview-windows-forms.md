---
title: Label, kontrolka — omówienie
ms.date: 03/30/2017
f1_keywords:
- Label
helpviewer_keywords:
- images [Windows Forms], displaying in labels
- labels
- Label control [Windows Forms], about Label control
ms.assetid: dcad7f44-11b7-4c55-b0c0-d984ade43d7d
ms.openlocfilehash: 1ca14553c7cb51d2b7a329950aeaec4c0439762a
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76745286"
---
# <a name="label-control-overview-windows-forms"></a>Label — Informacje o formancie (Formularze systemu Windows)
Kontrolki <xref:System.Windows.Forms.Label> Windows Forms są używane do wyświetlania tekstu lub obrazów, które nie mogą być edytowane przez użytkownika. Służą one do identyfikowania obiektów w formularzu — w celu udostępnienia opisu działania określonej kontrolki, na przykład, lub wyświetlenia informacji w odpowiedzi na zdarzenie lub proces w czasie wykonywania w aplikacji. Na przykład można użyć etykiet, aby dodać opisowe podpisy do pól tekstowych, pól listy, pól kombi i tak dalej. Możesz również napisać kod, który zmienia tekst wyświetlany przez etykietę w odpowiedzi na zdarzenia w czasie wykonywania. Jeśli na przykład aplikacja zajmie kilka minut, aby przetworzyć zmianę, można wyświetlić komunikat o stanie przetwarzania w etykiecie.  
  
## <a name="working-with-the-label-control"></a>Praca z kontrolką etykieta  
 Ponieważ formant <xref:System.Windows.Forms.Label> nie może odebrać fokusu, można go również użyć do utworzenia kluczy dostępu dla innych kontrolek. Klucz dostępu umożliwia użytkownikowi wybranie innej kontrolki przez naciśnięcie klawisza ALT z klawiszem dostępu. Aby uzyskać więcej informacji, zobacz [Tworzenie kluczy dostępu dla formantów Windows Forms](how-to-create-access-keys-for-windows-forms-controls.md) i [instrukcje: tworzenie kluczy dostępu za pomocą Windows Forms kontrolek etykiet](how-to-create-access-keys-with-windows-forms-label-controls.md).  
  
 Podpis wyświetlany w etykiecie jest zawarty we właściwości <xref:System.Windows.Forms.Label.Text%2A>. Właściwość <xref:System.Windows.Forms.Label.TextAlign%2A> pozwala ustawić wyrównanie tekstu w etykiecie. Aby uzyskać więcej informacji, zobacz [jak to zrobić: Ustawianie tekstu wyświetlanego przez kontrolkę Windows Forms](how-to-set-the-text-displayed-by-a-windows-forms-control.md).  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.Label>
- [Instrukcje: zmiana rozmiaru kontrolki Label formularzy Windows Forms w celu dopasowania jej do zawartości](how-to-size-a-windows-forms-label-control-to-fit-its-contents.md)
- [Instrukcje: tworzenie klawiszy dostępu za pomocą kontrolek Label formularzy Windows Forms](how-to-create-access-keys-with-windows-forms-label-controls.md)
