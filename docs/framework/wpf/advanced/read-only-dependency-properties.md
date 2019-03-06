---
title: Właściwości zależności tylko do odczytu
ms.date: 03/30/2017
helpviewer_keywords:
- dependency properties [WPF], read-only
- read-only dependency properties [WPF]
ms.assetid: f23d6ec9-3780-4c09-a2ff-b2f0a2deddf1
ms.openlocfilehash: 9aeeab95342bce94c53e89229003f55009118f96
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2019
ms.locfileid: "57379015"
---
# <a name="read-only-dependency-properties"></a>Właściwości zależności tylko do odczytu
W tym temacie opisano właściwości zależności tylko do odczytu, w tym istniejących właściwości zależności tylko do odczytu i scenariuszy i techniki tworzenia właściwości niestandardowej zależności tylko do odczytu.  
  

  
<a name="prerequisites"></a>   
## <a name="prerequisites"></a>Wymagania wstępne  
 W tym temacie założono, że rozumiesz podstawowe scenariusze Implementowanie właściwości zależności i sposób stosowania metadanych właściwości zależności niestandardowej. Zobacz [niestandardowe właściwości zależności](custom-dependency-properties.md) i [metadane zależności właściwości](dependency-property-metadata.md) dla kontekstu.  
  
<a name="existing"></a>   
## <a name="existing-read-only-dependency-properties"></a>Istniejące właściwości zależności tylko do odczytu  
 Niektóre właściwości zależności zdefiniowane w [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] framework są przeznaczone tylko do odczytu. Typową przyczyną do określania właściwości zależności tylko do odczytu jest, że są one właściwości, które mają być używane do określenia stanu, ale gdy ten stan ma wpływ wiele czynników, ale tylko ustawienie właściwości do tego stanu nie jest pożądane z Perspektywa projektowania interfejsu użytkownika. Na przykład właściwość <xref:System.Windows.UIElement.IsMouseOver%2A> jest tylko dzięki czemu są ujawniane stanu zgodnie z myszy dane wejściowe. Każda próba programowo ustawić tę wartość, przez obejście wejście myszy wartość true, będzie nieprzewidywalny i może spowodować niespójność.  
  
 Bycia nie można ustawić, właściwości zależności tylko do odczytu nie są odpowiednie dla wielu scenariuszy, dla których zależności właściwości oferują zwykle rozwiązanie (to znaczy: wiązanie bezpośrednio określonych stylach wartość, sprawdzania poprawności, animacji, dziedziczenie danych). Mimo iż nie można ustawić, tylko do odczytu zależności właściwości nadal mieć niektóre dodatkowe funkcje obsługiwane przez właściwości zależności w systemie właściwości. Najważniejsze możliwości pozostałe to, że właściwości zależności tylko do odczytu mogą być nadal używane jako wyzwalacz właściwości w stylu. Nie można włączyć wyzwalaczy zwykłym [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] właściwości musi być właściwość zależności. Wyżej wymienionych <xref:System.Windows.UIElement.IsMouseOver%2A> właściwość jest idealny przykład scenariusz, w którym może być bardzo przydatne do definiowania stylów dla kontrolki, gdy niektóre właściwości visible, takie jak tło, pierwszy plan lub podobne właściwości złożone elementów w obrębie Kontrolka ulegnie zmianie po użytkownik umieszcza myszy nad niektóre zdefiniowany region kontroli nad. Zmiany we właściwości zależności tylko do odczytu można również wykryte i podanych przez system właściwości nieprzerwaną pracę unieważniania procesów, a to w rzeczywistości obsługuje funkcje wyzwalacza właściwości wewnętrznie.  
  
<a name="new"></a>   
## <a name="creating-custom-read-only-dependency-properties"></a>Tworzenie niestandardowe tylko do odczytu właściwości zależności  
 Upewnij się, zapoznaj się z sekcją powyżej dotyczące Dlaczego właściwości zależności tylko do odczytu nie będzie działać w wielu scenariuszach typowe właściwości zależności. Ale jeśli jest to odpowiedni scenariusz, możesz utworzyć własne właściwości zależności tylko do odczytu.  
  
 Większa część procesu tworzenia właściwości zależności tylko do odczytu jest taki sam, jak opisano w [niestandardowe właściwości zależności](custom-dependency-properties.md) i [implementować właściwość zależności](how-to-implement-a-dependency-property.md) tematów. Istnieją trzy ważne różnice:  
  
-   Podczas rejestrowania Twoja własność, wywołaj <xref:System.Windows.DependencyProperty.RegisterReadOnly%2A> metody zamiast normalnych <xref:System.Windows.DependencyProperty.Register%2A> metodę rejestracji właściwości.  
  
-   Podczas implementowania [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] właściwość "otoki", upewnij się, że otoki zbyt nie zawiera implementacji zestawu, tak, aby w stanie tylko do odczytu dla otoki publiczny ma niezgodności należy udostępnić.  
  
-   Obiekt zwrócony przez rejestrację tylko do odczytu jest <xref:System.Windows.DependencyPropertyKey> zamiast <xref:System.Windows.DependencyProperty>. Nadal należy przechowywać w tym polu jako członka, ale zazwyczaj można nie zwiększyłoby publicznej składowej typu.  
  
 Niezależnie od prywatnych pola lub wartość ma zapasowy swoje właściwości zależności tylko do odczytu oczywiście można pełni zapisywalny, za pomocą dowolną logikę wymaganą zdecydujesz się. Jednak jest to najprostszy sposób ustaw właściwość początkowo lub jako część logiki czasu wykonywania do korzystania z systemu właściwości [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)], zamiast obejście system właściwości i ustawienia bezpośrednio do pola prywatnego pomocniczego. W szczególności, ma podpis <xref:System.Windows.DependencyObject.SetValue%2A> , które akceptuje parametr typu <xref:System.Windows.DependencyPropertyKey>. Jak i gdzie tę wartość ustawiono programowo w ramach logiki aplikacji będzie miało wpływ na sposób możesz ustawić dostęp na <xref:System.Windows.DependencyPropertyKey> tworzone podczas pierwszej rejestracji właściwość zależności. Jeśli obsługiwać tę logikę w klasie można wprowadzić prywatnej lub jeśli chcesz, należy ustawić z innych części zestawu można ustawić jego wewnętrznych. Jedno z podejść jest wywołanie <xref:System.Windows.DependencyObject.SetValue%2A> w ramach programu obsługi zdarzeń klasy istotne zdarzenia, informujący o wystąpienia klasy, który musi zostać zmienione wartości właściwości przechowywanej. Innym rozwiązaniem jest powiązanie właściwości zależności za pomocą sparowane <xref:System.Windows.PropertyChangedCallback> i <xref:System.Windows.CoerceValueCallback> wywołania zwrotne w ramach tych właściwości metadanych podczas rejestracji.  
  
 Ponieważ <xref:System.Windows.DependencyPropertyKey> jest prywatny i nie jest propagowany przez system właściwość poza swój kod, ma właściwości zależności tylko do odczytu, lepiej ustawienia zabezpieczeń niż właściwość zależności odczytu i zapisu. Dla właściwości zależności odczytu i zapisu pole identyfikacyjne jest jawnie lub niejawnie publiczny i więc właściwość jest szeroko do ustawienia. Aby uzyskać więcej szczegółowych informacji, zobacz [zabezpieczenia właściwości zależności](dependency-property-security.md).  
  
## <a name="see-also"></a>Zobacz także
- [Przegląd właściwości zależności](dependency-properties-overview.md)
- [Niestandardowe właściwości zależności](custom-dependency-properties.md)
- [Tworzenie szablonów i stylów](../controls/styling-and-templating.md)
