---
title: 'Instrukcje: Ustaw powiadomienie o łączeniu aktualizacji'
ms.date: 03/30/2017
helpviewer_keywords:
- notifications [WPF], binding updates
- data binding [WPF], notification of binding updates
- binding [WPF], updates [WPF], notifications of
ms.assetid: 5673073e-dbe1-49da-980a-484a88f9595a
ms.openlocfilehash: 0a28e6fc31601e881cf972f586f75ba0b1526b45
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2019
ms.locfileid: "57357966"
---
# <a name="how-to-set-up-notification-of-binding-updates"></a>Instrukcje: Ustaw powiadomienie o łączeniu aktualizacji
Ten przykład pokazuje, jak ustawić, aby otrzymywać powiadomienia, gdy cel wiążący (docelowy) lub właściwość source (źródło) powiązania powiązania został zaktualizowany.  
  
## <a name="example"></a>Przykład  
 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] zgłasza zdarzenie aktualizacji danych każdorazowo o zaktualizowaniu powiązania źródłowych lub docelowych. Wewnętrznie, to zdarzenie służy do informowania [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] który go zaktualizować, ponieważ została zmieniona powiązane dane. Uwaga dla tych zdarzeń do pracy, a także dla- lub dwukierunkowo powiązanie działało poprawnie, należy zaimplementować klasy dane przy użyciu <xref:System.ComponentModel.INotifyPropertyChanged> interfejsu. Aby uzyskać więcej informacji, zobacz [powiadomienie o zmianie właściwości Implementowanie](how-to-implement-property-change-notification.md).  
  
 Ustaw <xref:System.Windows.Data.Binding.NotifyOnTargetUpdated%2A> lub <xref:System.Windows.Data.Binding.NotifyOnSourceUpdated%2A> właściwości (lub obie) `true` w powiązaniu. Program obsługi, podane do nasłuchiwania pod kątem tego zdarzenia musi być dołączony bezpośrednio do elementu, którego powiadamiane o zmianach, lub ogólny kontekst danych, aby należy pamiętać, że niczego w kontekście zmieniła się.  
  
 Oto przykład pokazujący sposób konfigurowania powiadomienia, gdy właściwość docelowa została zaktualizowana.  
  
 [!code-xaml[DirectionalBinding#2](~/samples/snippets/csharp/VS_Snippets_Wpf/DirectionalBinding/CSharp/Page1.xaml#2)]  
  
 Następnie można przypisać obsługi, w oparciu o EventHandler\<T > delegować, *OnTargetUpdated* w tym przykładzie, aby obsłużyć zdarzenie:  
  
 [!code-csharp[DirectionalBinding#3](~/samples/snippets/csharp/VS_Snippets_Wpf/DirectionalBinding/CSharp/Page1.xaml.cs#3)]  
[!code-csharp[DirectionalBinding#EndEvent](~/samples/snippets/csharp/VS_Snippets_Wpf/DirectionalBinding/CSharp/Page1.xaml.cs#endevent)]  
  
 Aby określić szczegóły dotyczące właściwości, która się zmieniła (na przykład typ lub określony element, jeśli ten sam program obsługi jest podłączony do więcej niż jeden element), można użyć parametrów zdarzenia, które mogą być przydatne, jeśli ma wiele powiązanych właściwości na pojedynczy element.  
  
## <a name="see-also"></a>Zobacz także
- [Powiązanie danych — omówienie](data-binding-overview.md)
- [Tematy z instrukcjami](data-binding-how-to-topics.md)
