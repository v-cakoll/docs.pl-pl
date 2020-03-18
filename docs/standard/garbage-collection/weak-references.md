---
title: Słabe odwołania
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- weak references, short
- weak references, using
- weak references, long
- garbage collection, weak references
ms.assetid: 6a600fe5-3af3-4c64-82da-10a0a8e2d79b
ms.openlocfilehash: 120777ca3c26b1634bd2143863547cfa4ea5deac
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "73141334"
---
# <a name="weak-references"></a>Słabe odwołania
Moduł zbierający elementy bezużyteczne nie może zbierać obiektu używanego przez aplikację, podczas gdy kod aplikacji może dotrzeć do tego obiektu. Mówi się, że aplikacja ma silne odniesienie do obiektu.  
  
 Słabe odwołanie zezwala modułowi odśmiecania pamięci do zbierania obiektu, a jednocześnie umożliwia aplikacji dostęp do obiektu. Słabe odwołanie jest prawidłowy tylko w czasie nieokreślony czasu, dopóki obiekt jest zbierane, gdy nie istnieją silne odwołania. Korzystając z słabeodwołanie, aplikacja nadal można uzyskać silne odwołanie do obiektu, który uniemożliwia jego zbierania. Jednak zawsze istnieje ryzyko, że moduł zbierający elementy bezużyteczne przejdzie do obiektu najpierw przed ponownym ustanowieniem silnego odwołania.  
  
 Słabe odwołania są przydatne dla obiektów, które używają dużo pamięci, ale można je łatwo odtworzyć, jeśli są one odzyskane przez wyrzucanie elementów bezużytecznych.  
  
 Załóżmy, że widok drzewa w aplikacji Formularze systemu Windows wyświetla złożony hierarchiczny wybór opcji dla użytkownika. Jeśli dane źródłowe są duże, utrzymywanie drzewa w pamięci jest nieefektywne, gdy użytkownik jest zaangażowany w coś innego w aplikacji.  
  
 Gdy użytkownik przełącza się do innej części aplikacji, <xref:System.WeakReference> można użyć klasy, aby utworzyć słabe odwołanie do drzewa i zniszczyć wszystkie silne odwołania. Gdy użytkownik przełączy się z powrotem do drzewa, aplikacja próbuje uzyskać silne odwołanie do drzewa i, jeśli się powiedzie, unika rekonstrukcji drzewa.  
  
 Aby ustanowić słabe odwołanie z obiektem, należy utworzyć <xref:System.WeakReference> przy użyciu wystąpienia obiektu, który ma być śledzony. Następnie należy <xref:System.WeakReference.Target%2A> ustawić właściwość na ten obiekt i ustawić `null`oryginalne odwołanie do obiektu . Na przykład kodu <xref:System.WeakReference> zobacz w bibliotece klas.  
  
## <a name="short-and-long-weak-references"></a>Krótkie i długie słabe odniesienia  
 Można utworzyć krótkie słabe odniesienie lub długie słabe odniesienie:  
  
- Krótki  
  
     Obiekt docelowy krótkiego słabe `null` odwołanie staje się, gdy obiekt jest odzyskiwany przez wyrzucanie elementów bezużytecznych. Słabe odwołanie jest sam obiekt zarządzany i podlega wyrzucania elementów bezużytecznych, podobnie jak każdy inny obiekt zarządzany.  Krótkie słabe odwołanie jest konstruktorem bezparametrów dla <xref:System.WeakReference>.  
  
- Długi  
  
     Długie słabe odwołanie jest zachowywane po <xref:System.Object.Finalize%2A> wywołaniu metody obiektu. Dzięki temu obiekt ma zostać odtworzony, ale stan obiektu pozostaje nieprzewidywalny. Aby użyć odwołania długiego, należy określić `true` w <xref:System.WeakReference> konstruktorze.  
  
     Jeśli typ obiektu nie ma <xref:System.Object.Finalize%2A> metody, stosuje się funkcję krótkiego słabego odwołania, a słabe odwołanie jest prawidłowe tylko do momentu zebrania obiektu docelowego, co może wystąpić w dowolnym momencie po uruchomieniu finalizatora.  
  
 Aby ustanowić silne odwołanie i ponownie <xref:System.WeakReference.Target%2A> użyć obiektu, rzutować właściwość typu <xref:System.WeakReference> do typu obiektu. Jeśli <xref:System.WeakReference.Target%2A> właściwość `null`zwraca , obiekt został zebrany; w przeciwnym razie można nadal używać obiektu, ponieważ aplikacja odzyskał silne odwołanie do niego.  
  
## <a name="guidelines-for-using-weak-references"></a>Wskazówki dotyczące używania słabych odniesień  
 Użyj długich słabych odwołań tylko wtedy, gdy jest to konieczne, ponieważ stan obiektu jest nieprzewidywalny po zakończeniu.  
  
 Należy unikać używania słabych odwołań do małych obiektów, ponieważ sam wskaźnik może być tak duży lub większy.  
  
 Należy unikać używania słabych odwołań jako automatycznego rozwiązania problemów z zarządzaniem pamięcią. Zamiast tego opracuj skuteczne zasady buforowania do obsługi obiektów aplikacji.  
  
## <a name="see-also"></a>Zobacz też

- [Odzyskiwanie pamięci](../../../docs/standard/garbage-collection/index.md)
