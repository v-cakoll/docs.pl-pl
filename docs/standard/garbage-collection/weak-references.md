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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 65492beb888da1986f456d3fd000fc02f340f3c4
ms.sourcegitcommit: 4b6490b2529707627ad77c3a43fbe64120397175
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/10/2018
ms.locfileid: "44264964"
---
# <a name="weak-references"></a>Słabe odwołania
Moduł odśmiecania pamięci nie można zebrać obiekt używany przez aplikację, gdy kod aplikacji może osiągnąć tego obiektu. Aplikacja jest nazywany ma silne odwołanie do obiektu.  
  
 Słabe odwołanie zezwala na moduł odśmiecania pamięci, aby zbierać obiektu, wciąż zezwalając aplikacjom dostępu do obiektu. Słabe odwołanie jest prawidłowy tylko podczas nieokreślony ilość czasu, dopóki obiekt jest tworzona, gdy nie istnieją żadne odniesienia silne. Gdy używasz słabe odwołanie, aplikacja nadal można uzyskać silne odwołanie do obiektu, który uniemożliwia są zbierane. Jednak zawsze istnieje ryzyko, że moduł zbierający elementy bezużyteczne otrzyma obiektowi najpierw przed ustanowieniu silne odwołanie.  
  
 Słabe odwołania są przydatne dla obiektów, które używa dużej ilości pamięci, ale może być odtworzona łatwo, jeśli są odzyskiwane przez wyrzucanie elementów bezużytecznych.  
  
 Załóżmy, że widok drzewa w aplikacji Windows Forms Wyświetla złożonych hierarchiczne opcje do wyboru dla użytkownika. W przypadku dużych danych bazowych, utrzymywanie drzewa w pamięci jest nieefektywne po użytkownik jest związany z innych obiektów w aplikacji.  
  
 Jeśli użytkownik przejdzie natychmiast do innej części aplikacji, możesz użyć <xref:System.WeakReference> klasy, aby tworzyć słabe odwołanie do drzewa i niszczyć wszystkie odwołania silne. Gdy użytkownik zmienia powrót do drzewa, aplikacja próbuje uzyskać silne odwołanie do drzewa i jeśli to się powiedzie, pozwala uniknąć Rekonstruowanie drzewa.  
  
 Aby ustanowić słabe odwołanie z obiektu, należy utworzyć <xref:System.WeakReference> mają być śledzone za pomocą wystąpienia obiektu. Następnie ustawiamy <xref:System.WeakReference.Target%2A> właściwości tego obiektu i zestawu, oryginalnym odwoływać się do obiektu, aby `null`. Dla przykładu kodu zobacz <xref:System.WeakReference> w bibliotece klas.  
  
## <a name="short-and-long-weak-references"></a>Krótko- i długo słabe odwołania  
 Można utworzyć krótkiej słabe odwołanie lub długo słabe odwołanie:  
  
-   Krótka  
  
     Staje się celem krótki słabe odwołanie `null` gdy obiekt jest odzyskiwane przez wyrzucanie elementów bezużytecznych. Słabe odwołanie jest sam obiekt zarządzany i podlega wyrzucania elementów bezużytecznych, podobnie jak inne zarządzanego obiektu.  Krótkie słabe odwołanie jest domyślny konstruktor dla <xref:System.WeakReference>.  
  
-   długi  
  
     Długi słabe odwołanie jest zachowywane po obiektu <xref:System.Object.Finalize%2A> została wywołana metoda. Dzięki temu obiekt do odtworzenia, ale stan obiektu jest nieprzewidywalne. Aby użyć długie odwołania, określ `true` w <xref:System.WeakReference> konstruktora.  
  
     Jeśli nie ma typu obiektu <xref:System.Object.Finalize%2A> metody, funkcja krótki słabe odwołanie ma zastosowanie i słabe odwołanie jest prawidłowy tylko do momentu docelowej są zbierane, co może nastąpić w dowolnej chwili po finalizator uruchomieniu.  
  
 Aby ustanowić silne odwołanie i ponownie użyć obiektu, należy rzutować <xref:System.WeakReference.Target%2A> właściwość <xref:System.WeakReference> pod kątem typu obiektu. Jeśli <xref:System.WeakReference.Target%2A> właściwość zwraca `null`, obiekt był zebrane; w przeciwnym razie, możesz użyć obiektu, ponieważ aplikacja została ponownie nawiązana silne odwołanie do niego.  
  
## <a name="guidelines-for-using-weak-references"></a>Wskazówki dotyczące używania słabe odwołania  
 Użyj długo słabe odwołania, tylko wtedy, gdy jest to konieczne, ponieważ stan obiektu po zakończeniu, będzie nieprzewidywalny.  
  
 Należy unikać używania słabe odwołania do małych obiektów, ponieważ sam wskaźnik może być tak duży lub większe.  
  
 Należy unikać używania słabe odwołania jako rozwiązanie z automatycznego na problemy z zarządzaniem pamięcią. Zamiast tego należy opracować efektywnych zasad buforowania, obsługi obiektów Twojej aplikacji.  
  
## <a name="see-also"></a>Zobacz także

- [Odzyskiwanie pamięci](../../../docs/standard/garbage-collection/index.md)
