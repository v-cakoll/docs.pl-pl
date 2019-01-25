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
ms.openlocfilehash: eb27f3c902a0fb783d26d14d1ce494eebcffb999
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54532152"
---
# <a name="dependency-property-security"></a>Zabezpieczenie właściwości zależności
Właściwości zależności powinien ogólnie być uważane właściwości publiczne. Rodzaj [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] system właściwości zapobiega możliwość zapewnienia gwarancje bezpieczeństwa informacji na temat wartości właściwości zależności.  
  
  
<a name="AccessSecurity"></a>   
## <a name="access-and-security-of-wrappers-and-dependency-properties"></a>Dostęp i większe bezpieczeństwo otoki i właściwości zależności  
 Zazwyczaj właściwości zależności są implementowane wraz z "otoki" [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] właściwości, które upraszczają pobieranie lub ustawianie właściwości z wystąpienia usługi. Ale otoki metodami naprawdę jedynie jako udogodnienie implementacji podstawowych <xref:System.Windows.DependencyObject.GetValue%2A> i <xref:System.Windows.DependencyObject.SetValue%2A> wywołania statycznych, które są używane podczas interakcji z właściwości zależności. Myśl ją w inny sposób, właściwości są widoczne jako [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] właściwości, które odbywa się kopii właściwości zależności, a nie pola prywatnego. Mechanizmy zabezpieczeń stosowane do otoki nie równoległe właściwości zachowania systemu oraz dostępem do właściwości zależności. Umieszczenie żądania zabezpieczeń na otokę tylko uniemożliwi użycie wygodna metoda, ale nie uniemożliwia wywołania <xref:System.Windows.DependencyObject.GetValue%2A> lub <xref:System.Windows.DependencyObject.SetValue%2A>. Podobnie umieszczając chronione lub poziom dostępu prywatnego otoki nie zapewnia żadnych efektywnym elementem systemu zabezpieczeń.  
  
 Jeśli piszesz właściwości zależności, należy zadeklarować otoki i <xref:System.Windows.DependencyProperty> identyfikator pola jako publiczne elementy członkowskie, tak aby obiekty wywołujące nie uzyskać nieprawdziwych informacji o poziomie dostępu true właściwości (ze względu na jej magazynu jest zaimplementowane jako właściwość zależności).  
  
 Dla właściwości zależności niestandardowej, należy zarejestrować swoje właściwości jako właściwości zależności tylko do odczytu, a to zapewnić skuteczne środki zapobieganie właściwością przez dowolną osobę, która nie zawiera odwołania do <xref:System.Windows.DependencyPropertyKey> dla tej właściwości. Aby uzyskać więcej informacji, zobacz [właściwości zależności tylko do odczytu](../../../../docs/framework/wpf/advanced/read-only-dependency-properties.md).  
  
> [!NOTE]
>  Deklarowanie <xref:System.Windows.DependencyProperty> prywatnego pola Identyfikator jest niedozwolona, jego wielkiego można zmniejszyć bezpośrednio narażonych przestrzeni nazw, klasy niestandardowej, ale takiej właściwości nie powinny być uwzględniane w tym samym znaczeniu jako "private" [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] język definicje definiują ten poziom dostępu powodów opisanych w następnej sekcji.  
  
<a name="PropertySystemExposure"></a>   
## <a name="property-system-exposure-of-dependency-properties"></a>Właściwość systemu narażenia właściwości zależności  
 Nie jest to zazwyczaj przydatne i jest potencjalnie może być mylące, aby zadeklarować <xref:System.Windows.DependencyProperty> wszelkie dostęp na poziomie innych niż publicznego. To ustawienie poziomie dostępu tylko zapobiega ktoś można pobrać odwołania do wystąpienia z deklarującego klasy. Ale istnieją różne aspekty systemu właściwość, która zwróci <xref:System.Windows.DependencyProperty> jako sposób identyfikowania danej właściwości, ponieważ znajduje się na wystąpienie klasy lub wystąpienia klasy pochodnej, a ten identyfikator jest nadal można używać w <xref:System.Windows.DependencyObject.SetValue%2A> nawet wywołania Jeśli oryginalny identyfikator statycznego jest zadeklarowany jako nonpublic. Ponadto <xref:System.Windows.DependencyObject.OnPropertyChanged%2A> metod wirtualnych otrzymywanie informacji, wszelkie istniejące właściwości zależności, która się zmieniła wartość. Ponadto <xref:System.Windows.DependencyObject.GetLocalValueEnumerator%2A> metoda zwraca identyfikatorów dla wszystkich właściwości w wystąpieniach będzie używanych lokalnie ustawionej wartości.  
  
### <a name="validation-and-security"></a>Sprawdzanie poprawności i zabezpieczeń  
 Żądanie do stosowania <xref:System.Windows.DependencyProperty.ValidateValueCallback%2A> , a oczekiwano niepowodzenia weryfikacji w przypadku niepowodzenia żądanie, aby uniemożliwić ustawiania właściwości nie jest mechanizm odpowiednie zabezpieczenia. Ustaw wartość unieważniania wymuszane za pośrednictwem <xref:System.Windows.DependencyProperty.ValidateValueCallback%2A> również można pominąć przez złośliwe obiekty wywołujące, jeśli działają tych wywołań w domenie aplikacji.  
  
## <a name="see-also"></a>Zobacz także
- [Niestandardowe właściwości zależności](../../../../docs/framework/wpf/advanced/custom-dependency-properties.md)
