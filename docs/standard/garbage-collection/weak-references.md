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
ms.openlocfilehash: 4b7e7a62b92b2c685ff39baa75f4bc33602b5da2
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2020
ms.locfileid: "84287587"
---
# <a name="weak-references"></a>Słabe odwołania
Moduł wyrzucania elementów bezużytecznych nie może zebrać obiektu, który jest używany przez aplikację, gdy kod aplikacji może dotrzeć do tego obiektu. Aplikacja ma silne odwołanie do obiektu.  
  
 Słabe odwołanie umożliwia modułowi wyrzucania elementów bezużytecznych zbieranie obiektu, a jednocześnie pozwala aplikacji na dostęp do obiektu. Słabe odwołanie jest prawidłowe tylko w nieokreślonym czasie do momentu zebrania obiektu, gdy nie istnieją silne odwołania. W przypadku użycia słabego odwołania aplikacja może nadal uzyskać silne odwołanie do obiektu, co uniemożliwia jego zebranie. Jednak zawsze istnieje ryzyko, że moduł zbierający elementy bezużyteczne uzyska najpierw do obiektu przed ponownym ustanowieniem silnego odwołania.  
  
 Słabe odwołania są przydatne w przypadku obiektów, które korzystają z dużej ilości pamięci, ale można je odtworzyć, jeśli są odzyskiwane przez wyrzucanie elementów bezużytecznych.  
  
 Załóżmy, że widok drzewa w aplikacji Windows Forms wyświetla skomplikowaną hierarchiczną opcję opcji dla użytkownika. Jeśli dane podstawowe są duże, utrzymywanie drzewa w pamięci jest nieefektywne, gdy użytkownik korzysta z innego elementu w aplikacji.  
  
 Gdy użytkownik przełączy się do innej części aplikacji, można użyć <xref:System.WeakReference> klasy, aby utworzyć słabe odwołanie do drzewa i zniszczyć wszystkie silne odwołania. Gdy użytkownik przełącza się z powrotem do drzewa, aplikacja próbuje uzyskać silne odwołanie do drzewa i, jeśli to się powiedzie, unika odbudowy drzewa.  
  
 Aby ustanowić słabe odwołanie do obiektu, należy utworzyć <xref:System.WeakReference> wystąpienie obiektu, które ma być śledzone. Następnie ustawisz <xref:System.WeakReference.Target%2A> Właściwość na ten obiekt i ustawisz oryginalne odwołanie do obiektu `null` . Aby zapoznać się z przykładem kodu, zobacz <xref:System.WeakReference> w bibliotece klas.  
  
## <a name="short-and-long-weak-references"></a>Krótkie i długie słabe odwołania  
 Można utworzyć krótkie odwołanie słabe lub długie, słabe odwołanie:  
  
- Wybierak  
  
     Obiekt docelowy krótkiego słabego odwołania zostaje przerzucony `null` po odbraniu obiektu przez wyrzucanie elementów bezużytecznych. Słabe odwołanie jest samym obiektem zarządzanym i podlega wyrzucaniu elementów bezużytecznych, podobnie jak każdy inny obiekt zarządzany.  Krótkie, słabe odwołanie jest konstruktorem bez parametrów dla <xref:System.WeakReference> .  
  
- Długo  
  
     Po wywołaniu metody obiektu jest zachowywane długie odwołanie <xref:System.Object.Finalize%2A> . Pozwala to na odtworzenie obiektu, ale stan obiektu pozostaje nieprzewidywalny. Aby użyć długich odwołań, należy określić `true` w <xref:System.WeakReference> konstruktorze.  
  
     Jeśli typ obiektu nie ma <xref:System.Object.Finalize%2A> metody, stosowana jest krótka funkcja referencyjna odniesienia, a słabe odwołanie jest prawidłowe tylko do momentu zebrania elementu docelowego, co może wystąpić w dowolnym momencie po uruchomieniu finalizatora.  
  
 Aby ustanowić silną referencję i ponownie użyć obiektu, należy rzutować <xref:System.WeakReference.Target%2A> Właściwość a <xref:System.WeakReference> na typ obiektu. Jeśli <xref:System.WeakReference.Target%2A> Właściwość zwraca `null` , obiekt został zebrany; w przeciwnym razie można nadal używać obiektu, ponieważ aplikacja odzyskuje do niego silne odwołanie.  
  
## <a name="guidelines-for-using-weak-references"></a>Wskazówki dotyczące używania słabych odwołań  
 Używaj długich niesłabych odwołań tylko wtedy, gdy jest to konieczne, ponieważ stan obiektu jest nieprzewidywalny po zakończeniu finalizacji.  
  
 Unikaj używania słabych odwołań do małych obiektów, ponieważ sama wartość wskaźnika może być duża lub większa.  
  
 Unikaj używania słabych odwołań jako automatyczne rozwiązanie do problemów z zarządzaniem pamięcią. Zamiast tego należy opracować efektywne zasady buforowania do obsługi obiektów aplikacji.  
  
## <a name="see-also"></a>Zobacz także

- [Odzyskiwanie pamięci](index.md)
