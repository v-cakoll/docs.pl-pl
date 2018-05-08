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
ms.openlocfilehash: 2272220917f2d5adf15f1ba84a5d4c3d0ec07165
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="errorprovider-component-overview-windows-forms"></a>ErrorProvider — Informacje o składniku (Formularze systemu Windows)
Formularze systemu Windows [ErrorProvider](../../../../docs/framework/winforms/controls/errorprovider-component-windows-forms.md) składnika służy do sprawdzania poprawności danych wejściowych użytkownika dla formularza lub kontrolki. Jest ona zwykle używana w połączeniu z sprawdzanie poprawności danych wejściowych użytkownika dla formularza lub wyświetlanie błędów w elemencie dataset. Błąd dostawcy jest lepszym niż wyświetlanie komunikat o błędzie w oknie komunikatu, ponieważ gdy zostaje zamknięte okno komunikatu, komunikat o błędzie nie jest już widoczna. <xref:System.Windows.Forms.ErrorProvider> Składnika Wyświetla ikonę błędu (![ikona ErrorProvider](../../../../docs/framework/winforms/controls/media/vberrorprovidericon.gif "vbErrorProviderIcon")) obok odpowiednie urządzenie, takie jak pole tekstowe; gdy użytkownik umieszcza kursor myszy nad błąd, etykietka pojawi się ikona, przedstawiający ciąg z komunikatem o.  
  
## <a name="key-properties"></a>Właściwości klucza  
 <xref:System.Windows.Forms.ErrorProvider> Składnika właściwości klucza są <xref:System.Windows.Forms.ErrorProvider.DataSource%2A>, <xref:System.Windows.Forms.ErrorProvider.ContainerControl%2A>, i <xref:System.Windows.Forms.ErrorProvider.Icon%2A>. Korzystając z <xref:System.Windows.Forms.ErrorProvider> składnika z formantów powiązanych z danymi <xref:System.Windows.Forms.ErrorProvider.ContainerControl%2A> właściwość musi mieć ustawioną odpowiedniego kontenera (zazwyczaj formularz systemu Windows) w kolejności, w celu wyświetlenia ikony błędu w formularzu składnika. Gdy składnik zostanie dodany w Projektancie <xref:System.Windows.Forms.ErrorProvider.ContainerControl%2A> właściwość jest ustawiona na formularzu zawierającego; Jeśli dodasz formantu w kodzie, należy skonfigurować ją samodzielnie.  
  
 <xref:System.Windows.Forms.ErrorProvider.Icon%2A> Właściwość można ustawić ikonę błędu niestandardowego, zamiast domyślnej. Gdy <xref:System.Windows.Forms.ErrorProvider.DataSource%2A> właściwość jest ustawiona, <xref:System.Windows.Forms.ErrorProvider> składnika można wyświetlić komunikaty o błędach dla zestawu danych. Metoda klucza <xref:System.Windows.Forms.ErrorProvider> składnik jest <xref:System.Windows.Forms.ErrorProvider.SetError%2A> metody, która określa ciąg z komunikatem o i gdzie powinna zostać wyświetlona ikona błędu.  
  
> [!NOTE]
>  <xref:System.Windows.Forms.ErrorProvider> Składnik nie zapewnia wbudowaną obsługę dla ułatwień dostępu klientów. Aby udostępnić aplikację, korzystając z tego składnika, musisz podać mechanizm dodatkowych, dostępny opinii.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Forms.ErrorProvider>  
 [Instrukcje: wyświetlanie błędów w elemencie DataSet za pomocą składnika ErrorProvider formularzy Windows Forms](../../../../docs/framework/winforms/controls/view-errors-within-a-dataset-with-wf-errorprovider-component.md)  
 [Instrukcje: wyświetlanie ikon błędów dotyczących weryfikacji formularza za pomocą składnika ErrorProvider formularzy Windows Forms](../../../../docs/framework/winforms/controls/display-error-icons-for-form-validation-with-wf-errorprovider.md)
