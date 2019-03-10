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
ms.openlocfilehash: 61a8d4baba35a7a8a8ae221b054029eb59107d0e
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/09/2019
ms.locfileid: "57716260"
---
# <a name="errorprovider-component-overview-windows-forms"></a>ErrorProvider — Informacje o składniku (Formularze systemu Windows)
Formularze Windows [ErrorProvider](errorprovider-component-windows-forms.md) składnika służy do sprawdzania poprawności danych wejściowych użytkownika dla formularza lub formantu. Jest ona zwykle używana w połączeniu z sprawdzania poprawności danych wejściowych użytkownika na formularzu lub wyświetlanie błędów w zestawie danych. Błąd dostawcy jest lepszym niż wyświetlanie komunikatu o błędzie w oknie komunikatu, ponieważ po zamknięciu okno komunikatu, komunikat o błędzie nie jest już widoczna. <xref:System.Windows.Forms.ErrorProvider> Składnika Wyświetla ikonę błędu (![ikonę ErrorProvider](./media/vberrorprovidericon.gif "vbErrorProviderIcon")) obok odpowiednie kontrolki, takie jak pole tekstowe; po użytkownik umieszcza wskaźnik myszy nad ikona błędu etykietka narzędzia zostanie wyświetlony ciąg komunikatu o błędzie.  
  
## <a name="key-properties"></a>Właściwości klucza  
 <xref:System.Windows.Forms.ErrorProvider> Są właściwości kluczy tego składnika <xref:System.Windows.Forms.ErrorProvider.DataSource%2A>, <xref:System.Windows.Forms.ErrorProvider.ContainerControl%2A>, i <xref:System.Windows.Forms.ErrorProvider.Icon%2A>. Korzystając z <xref:System.Windows.Forms.ErrorProvider> składnika za pomocą kontrolek powiązanych z danymi <xref:System.Windows.Forms.ErrorProvider.ContainerControl%2A> właściwość musi być równa odpowiedniego kontenera (zazwyczaj formularz Windows) w kolejności, w celu wyświetlania ikona błędu w formularzu składnika. Gdy składnik zostanie dodany w Projektancie <xref:System.Windows.Forms.ErrorProvider.ContainerControl%2A> właściwość jest ustawiona na formularzu zawierającego; Jeśli dodasz kontrolki w kodzie, należy ustawić go samodzielnie.  
  
 <xref:System.Windows.Forms.ErrorProvider.Icon%2A> Właściwość można ustawić ikonę błędów niestandardowych zamiast domyślnego. Gdy <xref:System.Windows.Forms.ErrorProvider.DataSource%2A> ustawiono właściwość <xref:System.Windows.Forms.ErrorProvider> składnika można wyświetlić komunikaty o błędach dla zestawu danych. Metoda klucza <xref:System.Windows.Forms.ErrorProvider> składnik to <xref:System.Windows.Forms.ErrorProvider.SetError%2A> metodę, która określa ciąg komunikatu o błędzie i gdzie powinna zostać wyświetlona ikona błędu.  
  
> [!NOTE]
>  <xref:System.Windows.Forms.ErrorProvider> Składnika nie zapewnia wbudowaną obsługę dla ułatwień dostępu klientów. Aby udostępnić aplikację, korzystając z tego składnika, należy podać mechanizm przesyłania opinii dodatkowe, dostępne.  
  
## <a name="see-also"></a>Zobacz także
- <xref:System.Windows.Forms.ErrorProvider>
- [Instrukcje: Wyświetl błędy w zestawie danych za pomocą składnika ErrorProvider formularzy Windows](view-errors-within-a-dataset-with-wf-errorprovider-component.md)
- [Instrukcje: Wyświetlanie ikon błędów weryfikacji formularza za pomocą składnika ErrorProvider formularzy Windows](display-error-icons-for-form-validation-with-wf-errorprovider.md)
