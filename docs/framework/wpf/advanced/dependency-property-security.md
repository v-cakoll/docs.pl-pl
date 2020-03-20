---
title: Zabezpieczenie właściwości zależności
ms.date: 03/30/2017
helpviewer_keywords:
- wrappers [WPF], access
- wrappers [WPF], security
- dependency properties [WPF], security
- security [WPF], wrappers
- validation [WPF], dependency properties
- dependency properties [WPF], access
- security [WPF], dependency properties
ms.assetid: d10150ec-90c5-4571-8d35-84bafa2429a4
ms.openlocfilehash: f5640b348ccd68819052f58756489489371862d0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186394"
---
# <a name="dependency-property-security"></a>Zabezpieczenie właściwości zależności
Właściwości zależności należy ogólnie uznać za właściwości publiczne. Charakter systemu [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] właściwości uniemożliwia możliwość tworzenia gwarancji zabezpieczeń o wartości właściwości zależności.  

<a name="AccessSecurity"></a>
## <a name="access-and-security-of-wrappers-and-dependency-properties"></a>Dostęp i bezpieczeństwo otoki i właściwości zależności  
 Zazwyczaj właściwości zależności są implementowane wraz z właściwościami "otoki" wspólnego środowiska wykonawczego języka (CLR), które upraszczają uzyskiwanie lub ustawianie właściwości z wystąpienia. Ale otoki są naprawdę tylko metody <xref:System.Windows.DependencyObject.GetValue%2A> wygody, które implementują podstawowe i <xref:System.Windows.DependencyObject.SetValue%2A> statyczne wywołania, które są używane podczas interakcji z właściwości zależności. Myśląc o tym w inny sposób, właściwości są udostępniane jako właściwości środowiska wykonawczego języka wspólnego (CLR), które są wspierane przez właściwość zależności, a nie przez pole prywatne. Mechanizmy zabezpieczeń stosowane do otoki nie są równoległe zachowanie systemu właściwości i dostęp do podstawowej właściwości zależności. Umieszczenie żądania zabezpieczeń na opakowaniu tylko uniemożliwi użycie metody wygody, ale <xref:System.Windows.DependencyObject.GetValue%2A> <xref:System.Windows.DependencyObject.SetValue%2A>nie uniemożliwi wywołania lub . Podobnie umieszczenie chronionego lub prywatnego poziomu dostępu na otokach nie zapewnia żadnych skutecznych zabezpieczeń.  
  
 Jeśli piszesz własne właściwości zależności, należy zadeklarować otoki <xref:System.Windows.DependencyProperty> i pole identyfikatora jako elementy członkowskie publiczne, tak aby obiekty wywołujące nie uzyskać wprowadzających w błąd informacji o poziomie rzeczywistego dostępu tej właściwości (ze względu na jego magazyn jest implementowany jako właściwość zależności).  
  
 Dla właściwości zależności niestandardowej można zarejestrować właściwość jako właściwość zależność tylko do odczytu, a to zapewnia skuteczny sposób zapobiegania <xref:System.Windows.DependencyPropertyKey> właściwości jest ustawiany przez nikogo, kto nie posiada odwołania do dla tej właściwości. Aby uzyskać więcej informacji, zobacz [Właściwości zależności tylko do odczytu](read-only-dependency-properties.md).  
  
> [!NOTE]
> Deklarowanie <xref:System.Windows.DependencyProperty> prywatnego pola identyfikatora nie jest zabronione i może być używane w celu zmniejszenia bezpośrednio narażonej przestrzeni nazw klasy niestandardowej, ale taka właściwość nie powinna być uważana za "prywatną" w tym samym znaczeniu, co definicje języka wspólnego (CLR) definiują ten poziom dostępu z powodów opisanych w następnej sekcji.  
  
<a name="PropertySystemExposure"></a>
## <a name="property-system-exposure-of-dependency-properties"></a>Ekspozycja właściwości systemu właściwości zależności  
 Nie jest ogólnie przydatne i potencjalnie mylące jest <xref:System.Windows.DependencyProperty> deklarowanie jako jakiegokolwiek poziomu dostępu innego niż publiczny. To ustawienie poziomu dostępu tylko uniemożliwia komuś możliwość uzyskania odwołania do wystąpienia z klasy deklarującej. Ale istnieje kilka aspektów systemu właściwości, <xref:System.Windows.DependencyProperty> który zwróci jako środek identyfikacji określonej właściwości, ponieważ istnieje w wystąpieniu wystąpienia klasy lub wystąpienia klasy pochodnej, a ten identyfikator jest nadal użyteczny w <xref:System.Windows.DependencyObject.SetValue%2A> wywołaniu, nawet jeśli oryginalny identyfikator statyczny jest zadeklarowany jako niepubliczny. Ponadto <xref:System.Windows.DependencyObject.OnPropertyChanged%2A> metody wirtualne odbierają informacje o dowolnej istniejącej właściwości zależności, która zmieniła wartość. Ponadto <xref:System.Windows.DependencyObject.GetLocalValueEnumerator%2A> metoda zwraca identyfikatory dla dowolnej właściwości w wystąpieniach o wartości ustawionej lokalnie.  
  
### <a name="validation-and-security"></a>Walidacja i bezpieczeństwo  
 Stosowanie żądania do <xref:System.Windows.DependencyProperty.ValidateValueCallback%2A> i oczekiwanie niepowodzenia sprawdzania poprawności na żądanie awarii, aby zapobiec właściwość jest ustawiona nie jest odpowiedni mechanizm zabezpieczeń. Unieważnienie wartości zestawu wymuszane za pośrednictwem <xref:System.Windows.DependencyProperty.ValidateValueCallback%2A> może być również pomijane przez złośliwych wywołujących, jeśli te wywołania działają w domenie aplikacji.  
  
## <a name="see-also"></a>Zobacz też

- [Niestandardowe właściwości zależności](custom-dependency-properties.md)
