---
title: ErrorProvider — Informacje o składniku (Formularze systemu Windows)
ms.date: 03/30/2017
f1_keywords:
- ErrorProvider
helpviewer_keywords:
- errors [Windows Forms], displaying to users
- error messages [Windows Forms], displaying
- ErrorProvider component [Windows Forms], about ErrorProvider component
ms.assetid: ced189f2-b5c8-46a7-a6f1-37f5af95dc99
ms.openlocfilehash: 3cfd3f306d4a18ce8a194b5197060fbca1d157d9
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69965287"
---
# <a name="errorprovider-component-overview-windows-forms"></a>ErrorProvider — Informacje o składniku (Formularze systemu Windows)
Windows Forms składnik [ErrorProvider](errorprovider-component-windows-forms.md) służy do sprawdzania poprawności danych wejściowych użytkownika w formularzu lub formancie. Jest zazwyczaj używany w połączeniu z walidacją danych wejściowych użytkownika w formularzu lub wyświetlaniem błędów w ramach zestawu danych. Dostawca błędów jest lepszym rozwiązaniem niż wyświetlenie komunikatu o błędzie w oknie komunikatu, ponieważ po odrzuceniu okna komunikatu komunikat o błędzie nie jest już widoczny. Składnik wyświetla ikonę błędu (![biały wykrzyknik](./media/errorprovider-component-overview-windows-forms/vb-error-provider-icon.gif)w czerwonym kółku) obok odpowiedniej kontrolki, takiej jak pole tekstowe; gdy użytkownik umieści wskaźnik myszy nad ikoną błędu, zostanie wyświetlona etykietka narzędzia. <xref:System.Windows.Forms.ErrorProvider> wyświetlanie ciągu komunikatu o błędzie.  
  
## <a name="key-properties"></a>Właściwości klucza  
 Właściwości klucza <xref:System.Windows.Forms.ErrorProvider.DataSource%2A> <xref:System.Windows.Forms.ErrorProvider.ContainerControl%2A>składnika to,, i <xref:System.Windows.Forms.ErrorProvider.Icon%2A>. <xref:System.Windows.Forms.ErrorProvider> Gdy składnik <xref:System.Windows.Forms.ErrorProvider> jest <xref:System.Windows.Forms.ErrorProvider.ContainerControl%2A> używany z kontrolkami powiązanymi z danymi, właściwość musi być ustawiona na odpowiedni kontener (zazwyczaj formularz systemu Windows), aby składnik wyświetlał ikonę błędu w formularzu. Po dodaniu składnika do projektanta <xref:System.Windows.Forms.ErrorProvider.ContainerControl%2A> właściwość jest ustawiana na zawierającą formularz; Jeśli dodasz kontrolkę w kodzie, musisz ustawić ją samodzielnie.  
  
 Dla <xref:System.Windows.Forms.ErrorProvider.Icon%2A> właściwości można ustawić niestandardową ikonę błędu zamiast wartości domyślnej. Gdy właściwość jest ustawiona, składnik może wyświetlać komunikaty o błędach dla zestawu danych. <xref:System.Windows.Forms.ErrorProvider> <xref:System.Windows.Forms.ErrorProvider.DataSource%2A> Kluczową metodą <xref:System.Windows.Forms.ErrorProvider> składnika <xref:System.Windows.Forms.ErrorProvider.SetError%2A> jest metoda, która określa ciąg komunikatu o błędzie i lokalizację, w której ma zostać wyświetlona ikona błędu.  
  
> [!NOTE]
> <xref:System.Windows.Forms.ErrorProvider> Składnik nie zapewnia wbudowanej obsługi dla klientów ułatwień dostępu. Aby aplikacja była dostępna podczas korzystania z tego składnika, należy podać dodatkowy, dostępny mechanizm przesyłania opinii.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.ErrorProvider>
- [Instrukcje: Wyświetlanie błędów w elemencie DataSet za pomocą składnika Windows Forms ErrorProvider](view-errors-within-a-dataset-with-wf-errorprovider-component.md)
- [Instrukcje: Wyświetlanie ikon błędów dotyczących walidacji formularza za pomocą składnika Windows Forms ErrorProvider](display-error-icons-for-form-validation-with-wf-errorprovider.md)
