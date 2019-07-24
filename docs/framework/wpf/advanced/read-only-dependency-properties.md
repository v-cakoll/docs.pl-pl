---
title: Właściwości zależności tylko do odczytu
ms.date: 03/30/2017
helpviewer_keywords:
- dependency properties [WPF], read-only
- read-only dependency properties [WPF]
ms.assetid: f23d6ec9-3780-4c09-a2ff-b2f0a2deddf1
ms.openlocfilehash: aa6893b100311ead74f610dd20f327d130dff74a
ms.sourcegitcommit: 24a4a8eb6d8cfe7b8549fb6d823076d7c697e0c6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/23/2019
ms.locfileid: "68401653"
---
# <a name="read-only-dependency-properties"></a>Właściwości zależności tylko do odczytu
W tym temacie opisano właściwości zależności tylko do odczytu, w tym istniejące właściwości zależności tylko do odczytu oraz scenariusze i techniki tworzenia niestandardowej właściwości zależności tylko do odczytu.  

<a name="prerequisites"></a>   
## <a name="prerequisites"></a>Wymagania wstępne  
 W tym temacie założono, że rozumiesz podstawowe scenariusze implementowania właściwości zależności oraz sposób stosowania metadanych do niestandardowej właściwości zależności. Zapoznaj się z [właściwościami zależności niestandardowych](custom-dependency-properties.md) i [metadanych właściwości zależności](dependency-property-metadata.md) dla kontekstu.  
  
<a name="existing"></a>   
## <a name="existing-read-only-dependency-properties"></a>Istniejące właściwości zależności tylko do odczytu  
 Niektóre właściwości zależności zdefiniowane w [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] strukturze są tylko do odczytu. Typowym powodem określania właściwości zależności tylko do odczytu są te właściwości, które powinny być używane do określania stanu, ale w których ten stan ma wpływ wiele czynników, ale po prostu ustawienie właściwości na ten stan nie jest pożądane z perspektywa projektowania interfejsu użytkownika. Na przykład właściwość <xref:System.Windows.UIElement.IsMouseOver%2A> jest w rzeczywistości właśnie umieszczana w stanie określonym na podstawie danych wejściowych myszy. Każda próba ustawienia tej wartości programowo poprzez obejście rzeczywistego wejścia myszy byłoby nieprzewidywalne i spowoduje niespójność.  
  
 Z uwagi na to, że właściwości zależności tylko do odczytu nie są odpowiednie dla wielu scenariuszy, dla których właściwości zależności zazwyczaj oferują rozwiązanie (mianowicie: powiązanie danych, bezpośrednio określonych stylach do wartości, walidacji, animacji, dziedziczenia). Mimo że właściwości zależności tylko do odczytu nie są jeszcze zdefiniowane, istnieją pewne dodatkowe możliwości obsługiwane przez właściwości zależności w systemie właściwości. Najważniejszym pozostałą możliwością jest, że właściwość zależności tylko do odczytu może nadal służyć jako wyzwalacz właściwości w stylu. Wyzwalaczy nie można włączyć za pomocą normalnej właściwości środowiska uruchomieniowego języka wspólnego (CLR); musi to być właściwość zależności. Wspomniana <xref:System.Windows.UIElement.IsMouseOver%2A> właściwość jest idealnym przykładem scenariusza, w którym może być bardzo przydatna do definiowania stylu kontrolki, gdzie niektóre widoczne właściwości, takie jak tło, pierwszy plan lub podobne właściwości elementów złożonych w ramach formant zostanie zmieniony, gdy użytkownik umieści wskaźnik myszy nad określonym regionem kontrolki. Zmiany w właściwości zależności tylko do odczytu mogą być również wykrywane i raportowane przez niewłaściwe procesy unieważniania systemu właściwości, a to w rzeczywistości obsługuje wewnętrznie funkcje wyzwalacza właściwości.  
  
<a name="new"></a>   
## <a name="creating-custom-read-only-dependency-properties"></a>Tworzenie niestandardowych właściwości zależności tylko do odczytu  
 Upewnij się, że zapoznaj się z sekcją powyżej, dlaczego właściwości zależności tylko do odczytu nie będą działały dla wielu typowych scenariuszy właściwości zależności. Jeśli jednak masz odpowiedni scenariusz, możesz utworzyć własną właściwość zależności tylko do odczytu.  
  
 Większość procesu tworzenia właściwości zależności tylko do odczytu jest taka sama jak opisana we [właściwościach zależności niestandardowych](custom-dependency-properties.md) i zaimplementuj tematy dotyczące [właściwości zależności](how-to-implement-a-dependency-property.md) . Istnieją trzy istotne różnice:  
  
- Podczas rejestrowania właściwości Wywołaj <xref:System.Windows.DependencyProperty.RegisterReadOnly%2A> metodę zamiast normalnej <xref:System.Windows.DependencyProperty.Register%2A> metody rejestracji właściwości.  
  
- Podczas implementowania właściwości CLR "otoka" Upewnij się, że otoka nie ma ustawionej implementacji, więc nie istnieje niespójność w stanie tylko do odczytu dla otoki publicznej, którą ujawniasz.  
  
- Obiekt zwrócony przez rejestrację tylko do odczytu jest <xref:System.Windows.DependencyPropertyKey> <xref:System.Windows.DependencyProperty>zamiast. To pole powinno być nadal przechowywane jako element członkowski, ale zazwyczaj nie można go utworzyć jako publicznego elementu członkowskiego typu.  
  
 Niezależnie od tego, jakie pole lub wartość jest używana do tworzenia kopii zapasowej właściwości zależności tylko do odczytu, może być w pełni zapisywalne przy użyciu dowolnej logiki. Jednak najbardziej bezpośrednim sposobem ustawienia właściwości, początkowo lub w ramach logiki środowiska uruchomieniowego, jest użycie interfejsów API systemu właściwości, zamiast omijania systemu właściwości i bezpośredniego ustawiania prywatnego pola zapasowego. W szczególności istnieje podpis <xref:System.Windows.DependencyObject.SetValue%2A> , który akceptuje parametr typu. <xref:System.Windows.DependencyPropertyKey> Jak i miejsce, w którym ta wartość jest ustawiana programowo w ramach logiki aplikacji, będzie mieć wpływ na sposób, <xref:System.Windows.DependencyPropertyKey> w jaki użytkownik może chcieć ustawić dostęp na utworzonym czasie po pierwszej rejestracji właściwości zależności. Jeśli ta logika jest obsługiwana w ramach klasy, można ją ustawić jako prywatną lub jeśli wymaga jej ustawienia z innych części zestawu, można ustawić ją jako wewnętrzną. Jednym z metod jest wywołanie <xref:System.Windows.DependencyObject.SetValue%2A> w ramach procedury obsługi zdarzeń klasy odpowiedniego zdarzenia, które informuje wystąpienie klasy o konieczności zmiany przechowywanej wartości właściwości. Innym podejściem jest powiązanie właściwości zależności przy użyciu par <xref:System.Windows.PropertyChangedCallback> i <xref:System.Windows.CoerceValueCallback> wywołań zwrotnych w ramach metadanych podczas rejestracji.  
  
 <xref:System.Windows.DependencyPropertyKey> Ponieważ jest to element prywatny i nie jest propagowany przez system właściwości poza kodem, właściwość zależności tylko do odczytu ma lepszą wartość zabezpieczenia niż właściwość zależności odczytu i zapisu. Dla właściwości zależności odczytu i zapisu pole identyfikacyjne jest jawnie lub niejawnie publiczne i w ten sposób właściwość jest szeroko settable. Aby uzyskać bardziej szczegółowe informacje, zobacz [zależność właściwości zależności](dependency-property-security.md).  
  
## <a name="see-also"></a>Zobacz także

- [Przegląd właściwości zależności](dependency-properties-overview.md)
- [Niestandardowe właściwości zależności](custom-dependency-properties.md)
- [Tworzenie szablonów i stylów](../controls/styling-and-templating.md)
