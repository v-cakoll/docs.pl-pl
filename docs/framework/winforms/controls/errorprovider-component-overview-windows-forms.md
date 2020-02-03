---
title: ErrorProvider, składnik — omówienie
ms.date: 03/30/2017
f1_keywords:
- ErrorProvider
helpviewer_keywords:
- errors [Windows Forms], displaying to users
- error messages [Windows Forms], displaying
- ErrorProvider component [Windows Forms], about ErrorProvider component
ms.assetid: ced189f2-b5c8-46a7-a6f1-37f5af95dc99
ms.openlocfilehash: b66e97d97d0d8c2ea4e9bdba29f8ff35e486e1f6
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76745791"
---
# <a name="errorprovider-component-overview-windows-forms"></a>ErrorProvider — Informacje o składniku (Formularze systemu Windows)
Windows Forms składnik [ErrorProvider](errorprovider-component-windows-forms.md) służy do sprawdzania poprawności danych wejściowych użytkownika w formularzu lub formancie. Jest zazwyczaj używany w połączeniu z walidacją danych wejściowych użytkownika w formularzu lub wyświetlaniem błędów w ramach zestawu danych. Dostawca błędów jest lepszym rozwiązaniem niż wyświetlenie komunikatu o błędzie w oknie komunikatu, ponieważ po odrzuceniu okna komunikatu komunikat o błędzie nie jest już widoczny. Składnik <xref:System.Windows.Forms.ErrorProvider> wyświetla ikonę błędu (![biały wykrzyknik w kolorze czerwonym.](./media/errorprovider-component-overview-windows-forms/vb-error-provider-icon.gif)) obok odpowiedniej kontrolki, takiej jak pole tekstowe; gdy użytkownik umieści wskaźnik myszy nad ikoną błędu, zostanie wyświetlona etykietka narzędzia zawierająca ciąg komunikatu o błędzie.  
  
## <a name="key-properties"></a>Właściwości klucza  
 Właściwości klucza składnika <xref:System.Windows.Forms.ErrorProvider> są <xref:System.Windows.Forms.ErrorProvider.DataSource%2A>, <xref:System.Windows.Forms.ErrorProvider.ContainerControl%2A>i <xref:System.Windows.Forms.ErrorProvider.Icon%2A>. W przypadku korzystania ze składnika <xref:System.Windows.Forms.ErrorProvider> z kontrolkami powiązanymi z danymi Właściwość <xref:System.Windows.Forms.ErrorProvider.ContainerControl%2A> musi być ustawiona na odpowiedni kontener (zazwyczaj formularz systemu Windows), aby składnik mógł wyświetlić ikonę błędu w formularzu. Po dodaniu składnika do projektanta Właściwość <xref:System.Windows.Forms.ErrorProvider.ContainerControl%2A> jest ustawiana na zawierającą formularz; Jeśli dodasz kontrolkę w kodzie, musisz ustawić ją samodzielnie.  
  
 Właściwość <xref:System.Windows.Forms.ErrorProvider.Icon%2A> można ustawić na niestandardową ikonę błędu zamiast wartości domyślnej. Po ustawieniu właściwości <xref:System.Windows.Forms.ErrorProvider.DataSource%2A> składnik <xref:System.Windows.Forms.ErrorProvider> może wyświetlać komunikaty o błędach dla zestawu danych. Kluczową metodą składnika <xref:System.Windows.Forms.ErrorProvider> jest metoda <xref:System.Windows.Forms.ErrorProvider.SetError%2A>, która określa ciąg komunikatu o błędzie i lokalizację, w której ma zostać wyświetlona ikona błędu.  
  
> [!NOTE]
> Składnik <xref:System.Windows.Forms.ErrorProvider> nie zapewnia wbudowanej obsługi dla klientów ułatwień dostępu. Aby aplikacja była dostępna podczas korzystania z tego składnika, należy podać dodatkowy, dostępny mechanizm przesyłania opinii.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.ErrorProvider>
- [Instrukcje: wyświetlanie błędów w elemencie DataSet za pomocą składnika ErrorProvider formularzy Windows Forms](view-errors-within-a-dataset-with-wf-errorprovider-component.md)
- [Instrukcje: wyświetlanie ikon błędów dotyczących weryfikacji formularza za pomocą składnika ErrorProvider formularzy Windows Forms](display-error-icons-for-form-validation-with-wf-errorprovider.md)
