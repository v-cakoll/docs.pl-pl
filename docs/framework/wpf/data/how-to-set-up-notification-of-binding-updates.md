---
title: Jak ustawić powiadomienie o łączeniu aktualizacji
ms.date: 03/30/2017
helpviewer_keywords:
- notifications [WPF], binding updates
- data binding [WPF], notification of binding updates
- binding [WPF], updates [WPF], notifications of
ms.assetid: 5673073e-dbe1-49da-980a-484a88f9595a
ms.openlocfilehash: dfa0f9264247f7585c1743e40fd980906556efd0
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/03/2019
ms.locfileid: "73454948"
---
# <a name="how-to-set-up-notification-of-binding-updates"></a>Jak ustawić powiadomienie o łączeniu aktualizacji
Ten przykład pokazuje, jak skonfigurować, aby otrzymywać powiadomienia o aktualizacji elementu docelowego powiązania (target) lub źródła powiązania (Źródło) powiązania.  
  
## <a name="example"></a>Przykład  
 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] zgłasza zdarzenie aktualizacji danych za każdym razem, gdy źródło lub cel powiązania zostały zaktualizowane. Wewnętrznie to zdarzenie służy do informowania [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)], że powinna zostać zaktualizowana, ponieważ dane powiązane zostały zmienione. Należy pamiętać, że w celu poprawnego działania tych zdarzeń, a także dla jednokierunkowego lub dwukierunkowego powiązania, należy zaimplementować klasę danych przy użyciu interfejsu <xref:System.ComponentModel.INotifyPropertyChanged>. Aby uzyskać więcej informacji, zobacz [implementacja powiadomienia o zmianie właściwości](how-to-implement-property-change-notification.md).  
  
 Ustaw właściwość <xref:System.Windows.Data.Binding.NotifyOnTargetUpdated%2A> lub <xref:System.Windows.Data.Binding.NotifyOnSourceUpdated%2A> (lub obie) na `true` w powiązaniu. Program obsługi, który zapewniasz nasłuchiwanie tego zdarzenia, musi zostać dołączony bezpośrednio do elementu, w którym chcesz otrzymywać informacje o zmianach lub do ogólnego kontekstu danych, jeśli chcesz mieć świadomość, że wszystkie elementy w kontekście uległy zmianie.  
  
 Oto przykład, w którym pokazano, jak skonfigurować dla powiadomienia, kiedy Właściwość docelowa została zaktualizowana.  
  
 [!code-xaml[DirectionalBinding#2](~/samples/snippets/csharp/VS_Snippets_Wpf/DirectionalBinding/CSharp/Page1.xaml#2)]  
  
 Następnie można przypisać procedurę obsługi na podstawie EventHandler\<T > delegata, *OnTargetUpdated* w tym przykładzie, aby obsłużyć zdarzenie:  
  
 [!code-csharp[DirectionalBinding#3](~/samples/snippets/csharp/VS_Snippets_Wpf/DirectionalBinding/CSharp/Page1.xaml.cs#3)]  
[!code-csharp[DirectionalBinding#EndEvent](~/samples/snippets/csharp/VS_Snippets_Wpf/DirectionalBinding/CSharp/Page1.xaml.cs#endevent)]  
  
 Parametry zdarzenia mogą służyć do określenia szczegółowych informacji o właściwości, która została zmieniona (na przykład typu lub konkretnego elementu, jeśli ta sama procedura obsługi jest dołączona do więcej niż jednego elementu), co może być przydatne, jeśli istnieje wiele właściwości powiązanych jednego elementu.  
  
## <a name="see-also"></a>Zobacz także

- [Powiązanie danych — omówienie](../../../desktop-wpf/data/data-binding-overview.md)
- [Tematy z instrukcjami](data-binding-how-to-topics.md)
