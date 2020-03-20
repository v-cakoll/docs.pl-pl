---
title: Właściwości zależności tylko do odczytu
ms.date: 03/30/2017
helpviewer_keywords:
- dependency properties [WPF], read-only
- read-only dependency properties [WPF]
ms.assetid: f23d6ec9-3780-4c09-a2ff-b2f0a2deddf1
ms.openlocfilehash: 8adc90182f0f42f52e6ace4e13c68acb3539516b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79187178"
---
# <a name="read-only-dependency-properties"></a>Właściwości zależności tylko do odczytu
W tym temacie opisano właściwości zależności tylko do odczytu, w tym istniejące właściwości zależności tylko do odczytu oraz scenariusze i techniki tworzenia niestandardowej właściwości zależności tylko do odczytu.  

<a name="prerequisites"></a>
## <a name="prerequisites"></a>Wymagania wstępne  
 W tym temacie przyjęto założenie, że rozumiesz podstawowe scenariusze implementacji właściwości zależności i jak metadane są stosowane do właściwości zależności niestandardowej. Zobacz [Właściwości zależności niestandardowej](custom-dependency-properties.md) i [metadane właściwości zależności](dependency-property-metadata.md) dla kontekstu.  
  
<a name="existing"></a>
## <a name="existing-read-only-dependency-properties"></a>Istniejące właściwości zależności tylko do odczytu  
 Niektóre właściwości zależności zdefiniowane w [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] ramach są tylko do odczytu. Typowym powodem określenia właściwości zależności tylko do odczytu jest to, że są to właściwości, które powinny być używane do określania stanu, ale gdzie ten stan jest pod wpływem wielu czynników, ale samo ustawienie właściwości do tego stanu nie jest pożądane z a perspektywy projektowania interfejsu użytkownika. Na przykład właściwość <xref:System.Windows.UIElement.IsMouseOver%2A> jest naprawdę tylko napawania stanu, jak określono na podstawie danych wejściowych myszy. Każda próba zaprogramowania tej wartości przez obejście prawdziwego wprowadzania danych myszy byłaby nieprzewidywalna i spowodowałaby niespójność.  
  
 Ze względu na nie jest settable właściwości zależności tylko do odczytu nie są odpowiednie dla wielu scenariuszy, dla których właściwości zależności zwykle oferują rozwiązanie (a mianowicie: powiązanie danych, bezpośrednio stylizowany na wartość, sprawdzanie poprawności, animacji, dziedziczenia). Mimo, że nie jest settable, tylko do odczytu właściwości zależności nadal niektóre dodatkowe możliwości obsługiwane przez właściwości zależności w systemie właściwości. Najważniejszą pozostałą możliwością jest to, że właściwość zależności tylko do odczytu może nadal służyć jako wyzwalacz właściwości w stylu. Nie można włączyć wyzwalaczy z właściwością normalnego środowiska wykonawczego języka wspólnego (CLR); musi być właściwością zależności. Powyższa <xref:System.Windows.UIElement.IsMouseOver%2A> właściwość jest doskonałym przykładem scenariusza, w którym może być bardzo przydatne do definiowania stylu formantu, gdzie niektóre widoczne właściwości, takie jak tło, pierwszy plan lub podobne właściwości elementów złożonych w formancie zmieni się, gdy użytkownik umieszcza mysz nad niektórych zdefiniowanych regionu formantu. Zmiany we właściwości zależności tylko do odczytu mogą być również wykrywane i zgłaszane przez nieodłączne procesy unieważnienia systemu właściwości, a to w rzeczywistości obsługuje funkcję wyzwalania właściwości wewnętrznie.  
  
<a name="new"></a>
## <a name="creating-custom-read-only-dependency-properties"></a>Tworzenie niestandardowych właściwości zależności tylko do odczytu  
 Upewnij się, aby przeczytać sekcję powyżej dotyczące dlaczego tylko do odczytu właściwości zależności nie będzie działać dla wielu typowych scenariuszy właściwości zależności. Ale jeśli masz odpowiedni scenariusz, możesz chcieć utworzyć własną właściwość zależności tylko do odczytu.  
  
 Większość procesu tworzenia właściwości zależności tylko do odczytu jest taka sama, jak jest opisana w [właściwości zależności niestandardowej](custom-dependency-properties.md) i [implementuj](how-to-implement-a-dependency-property.md) właściwości zależności tematów. Istnieją trzy ważne różnice:  
  
- Podczas rejestrowania właściwości, <xref:System.Windows.DependencyProperty.RegisterReadOnly%2A> wywołać metodę zamiast <xref:System.Windows.DependencyProperty.Register%2A> normalnej metody rejestracji właściwości.  
  
- Podczas implementowania właściwości "otoki" CLR upewnij się, że otoka też nie ma implementacji zestawu, tak aby nie wystąpiła niespójność w stanie tylko do odczytu dla publicznego otoki, które udostępniasz.  
  
- Obiekt zwrócony przez rejestrację <xref:System.Windows.DependencyPropertyKey> tylko <xref:System.Windows.DependencyProperty>do odczytu jest, a nie . To pole należy nadal przechowywać jako element członkowski, ale zazwyczaj nie należy go upubliczniać jako członka tego typu.  
  
 Niezależnie od prywatnego pola lub wartości masz kopię zapasową właściwości zależności tylko do odczytu może być oczywiście w pełni zapisywalny przy użyciu dowolnej logiki zdecydujesz. Jednak najprostszym sposobem, aby ustawić właściwość początkowo lub jako część logiki środowiska uruchomieniowego jest użycie interfejsów API systemu właściwości, a nie obejście systemu właściwości i ustawienie prywatnego pola zapasowego bezpośrednio. W szczególności istnieje <xref:System.Windows.DependencyObject.SetValue%2A> podpis, który akceptuje parametr <xref:System.Windows.DependencyPropertyKey>typu . Jak i gdzie ustawić tę wartość programowo w ramach logiki aplikacji wpłynie <xref:System.Windows.DependencyPropertyKey> na to, jak można ustawić dostęp na utworzone podczas pierwszego zarejestrowania właściwości zależności. Jeśli obsługujesz tę logikę w klasie można uczynić go prywatnym lub jeśli wymagasz, aby być ustawione z innych części zestawu można ustawić go wewnętrznego. Jednym z podejść jest wywołanie <xref:System.Windows.DependencyObject.SetValue%2A> w ramach programu obsługi zdarzeń klasy odpowiedniego zdarzenia, które informuje wystąpienie klasy, że wartość przechowywanej właściwości musi zostać zmieniona. Innym podejściem jest powiązanie właściwości zależności <xref:System.Windows.PropertyChangedCallback> razem <xref:System.Windows.CoerceValueCallback> przy użyciu sparowanych i wywołań zwrotnych jako część metadanych tych właściwości podczas rejestracji.  
  
 Ponieważ <xref:System.Windows.DependencyPropertyKey> jest prywatny i nie jest propagowany przez system właściwości poza kodem, właściwość zależności tylko do odczytu ma lepsze zabezpieczenia ustawień niż właściwość zależności odczytu i zapisu. Dla właściwości zależności odczytu i zapisu pole identyfikujące jest jawnie lub niejawnie publiczne, a zatem właściwość jest powszechnie ustawiona. Aby uzyskać więcej informacji, zobacz [Bezpieczeństwo właściwości zależności](dependency-property-security.md).  
  
## <a name="see-also"></a>Zobacz też

- [Przegląd Właściwości zależności](dependency-properties-overview.md)
- [Niestandardowe właściwości zależności](custom-dependency-properties.md)
- [Tworzenie szablonów i stylów](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
