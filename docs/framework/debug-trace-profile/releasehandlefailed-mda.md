---
title: releaseHandleFailed MDA
ms.date: 03/30/2017
helpviewer_keywords:
- managed debugging assistants (MDAs), handles
- release handle failed
- CriticalHandle class, run-time errors
- releaseHandleFailed MDA
- ReleaseHandle method
- SafeHandle class, run-time errors
- MDAs (managed debugging assistants), handles
ms.assetid: 44cd98ba-95e5-40a1-874d-e8e163612c51
ms.openlocfilehash: 268acb01a6777315829378e6fd8c06c46d3136d2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79181747"
---
# <a name="releasehandlefailed-mda"></a>releaseHandleFailed MDA
Asystent `releaseHandleFailed` debugowania zarządzanego (MDA) jest aktywowany <xref:System.Runtime.InteropServices.SafeHandle.ReleaseHandle%2A> jest powiadamianie deweloperów, gdy metoda klasy pochodzące z <xref:System.Runtime.InteropServices.SafeHandle> lub <xref:System.Runtime.InteropServices.CriticalHandle> zwraca `false`.  
  
## <a name="symptoms"></a>Objawy  
 Wycieki zasobów lub pamięci.  Jeśli <xref:System.Runtime.InteropServices.SafeHandle.ReleaseHandle%2A> metoda klasy pochodzące <xref:System.Runtime.InteropServices.SafeHandle> z <xref:System.Runtime.InteropServices.CriticalHandle> lub nie powiedzie się, a następnie zasób hermetyzowany przez klasę może nie zostały zwolnione lub oczyszczone.  
  
## <a name="cause"></a>Przyczyna  
 Użytkownicy muszą zapewnić <xref:System.Runtime.InteropServices.SafeHandle.ReleaseHandle%2A> implementację metody, jeśli tworzą <xref:System.Runtime.InteropServices.SafeHandle> <xref:System.Runtime.InteropServices.CriticalHandle>klasy, które wynikają z lub ; okoliczności te są specyficzne dla poszczególnych zasobów. Jednakże wymagania są następujące:  
  
- <xref:System.Runtime.InteropServices.SafeHandle>i <xref:System.Runtime.InteropServices.CriticalHandle> typy reprezentują otoki wokół ważnych zasobów procesu. Przeciek pamięci sprawi, że proces będzie bezużyteczny w czasie.  
  
- Metoda <xref:System.Runtime.InteropServices.SafeHandle.ReleaseHandle%2A> nie może nie spełniać swojej funkcji. Gdy proces nabywa taki zasób, jest jedynym sposobem, <xref:System.Runtime.InteropServices.SafeHandle.ReleaseHandle%2A> aby go zwolnić. W związku z tym błąd oznacza przecieki zasobów.  
  
- Każdy błąd, który występuje <xref:System.Runtime.InteropServices.SafeHandle.ReleaseHandle%2A>podczas wykonywania , utrudniając uwolnienie zasobu, jest błędem w implementacji samej <xref:System.Runtime.InteropServices.SafeHandle.ReleaseHandle%2A> metody. Jest odpowiedzialny za programistę, aby upewnić się, że umowa jest spełniona, nawet jeśli ten kod wywołuje kod autorstwa innej osoby do wykonywania jego funkcji.  
  
## <a name="resolution"></a>Rozwiązanie  
 Kod, który używa <xref:System.Runtime.InteropServices.SafeHandle> określonego <xref:System.Runtime.InteropServices.CriticalHandle>(lub) typu, który wywołał powiadomienie MDA powinny zostać poddane przeglądowi, <xref:System.Runtime.InteropServices.SafeHandle> szukając miejsc, w których wartość nieprzetworzonego dojścia jest wyodrębniany z i kopiowane w innym miejscu. Jest to zwykle przyczyną błędów w obrębie <xref:System.Runtime.InteropServices.SafeHandle> lub <xref:System.Runtime.InteropServices.CriticalHandle> implementacji, ponieważ użycie wartości uchwytu nieprzetworzonego jest następnie nie jest już śledzone przez środowisko wykonawcze. Jeśli kopia nieprzetworzonego dojścia <xref:System.Runtime.InteropServices.SafeHandle.ReleaseHandle%2A> jest następnie zamykana, może to spowodować niepowodzenie późniejszego wywołania, ponieważ próbuje się zamknąć na tym samym dojściu, który jest teraz nieprawidłowy.  
  
 Istnieje kilka sposobów, w których może wystąpić nieprawidłowe duplikacja uchwytu:  
  
- Poszukaj <xref:System.Runtime.InteropServices.SafeHandle.DangerousGetHandle%2A> wywołań metody. Wywołania tej metody powinny być niezwykle rzadkie, a wszelkie, które <xref:System.Runtime.InteropServices.SafeHandle.DangerousAddRef%2A> można <xref:System.Runtime.InteropServices.SafeHandle.DangerousRelease%2A> znaleźć powinny być otoczone wywołaniem i metod. Te te ostatnie metody określają region kodu, w którym wartość nieprzetworzonego dojścia może być bezpiecznie używana. Poza tym regionem lub jeśli liczba odwołań nigdy nie jest zwiększana w pierwszej kolejności, wartość <xref:System.Runtime.InteropServices.SafeHandle.Dispose%2A> dojścia może zostać unieważniona w dowolnym momencie przez wywołanie lub <xref:System.Runtime.InteropServices.SafeHandle.Close%2A> w innym wątku. Po wszystkich zastosowań <xref:System.Runtime.InteropServices.SafeHandle.DangerousGetHandle%2A> zostały wytropione, należy podążać ścieżką nieprzetworzonego uchwytu, aby upewnić `CloseHandle` się, że nie jest przekazywana do niektórych składników, które ostatecznie wywołać lub innej metody macierzystej niskiego poziomu, który zwolni dojście.  
  
- Upewnij się, że kod, który <xref:System.Runtime.InteropServices.SafeHandle> jest używany do inicjowania z prawidłową wartość nieprzetworzonego dojścia jest właścicielem dojścia. Jeśli tworzysz <xref:System.Runtime.InteropServices.SafeHandle> wokół dojścia kodu nie `ownsHandle` jest `false` właścicielem bez ustawiania parametru w konstruktorze podstawowym, a następnie <xref:System.Runtime.InteropServices.SafeHandle> właściciel <xref:System.Runtime.InteropServices.SafeHandle.ReleaseHandle%2A> dojścia i rzeczywistego można spróbować zamknąć dojście, co prowadzi do błędu w przypadku <xref:System.Runtime.InteropServices.SafeHandle> utraty wyścigu.  
  
- Gdy <xref:System.Runtime.InteropServices.SafeHandle> jest organizowane między domenami <xref:System.Runtime.InteropServices.SafeHandle> aplikacji, upewnij się, że używane wyprowadzanie zostało oznaczone jako serializable. W rzadkich przypadkach, gdy <xref:System.Runtime.InteropServices.SafeHandle> klasa pochodząca z została wykonana <xref:System.Runtime.Serialization.ISerializable> serializable, należy zaimplementować interfejs lub użyć jednej z innych technik do kontrolowania procesu serializacji i deserializacji ręcznie. Jest to wymagane, ponieważ domyślną akcję serializacji jest utworzenie bitowego klonu zamkniętej <xref:System.Runtime.InteropServices.SafeHandle> wartości nieprzetworzonego dojścia, co powoduje, że dwa wystąpienia myślą, że są właścicielami tego samego dojścia. Obie będą próbowały wywołać <xref:System.Runtime.InteropServices.SafeHandle.ReleaseHandle%2A> ten sam uchwyt w pewnym momencie. Drugi <xref:System.Runtime.InteropServices.SafeHandle> to zrobić nie powiedzie się. Prawidłowy kurs akcji podczas <xref:System.Runtime.InteropServices.SafeHandle> serializacji a `DuplicateHandle` jest wywołanie funkcji lub podobnej funkcji dla typu dojścia macierzystego, aby dokonać różnych kopii uchwyt prawny. Jeśli typ dojścia nie <xref:System.Runtime.InteropServices.SafeHandle> obsługuje tego następnie zawijania typu nie można dokonać serializable.  
  
- Może być możliwe śledzenie, gdzie dojście jest zamykany <xref:System.Runtime.InteropServices.SafeHandle.ReleaseHandle%2A> wcześnie, co prowadzi do awarii, gdy metoda jest ostatecznie wywoływana, umieszczając punkt `CloseHandle` przerwania debugera na natywnej procedury używane do zwalniania dojścia, na przykład funkcji. Może to nie być możliwe w przypadku scenariuszy warunków skrajnych, a nawet średnich testów funkcjonalnych ze względu na duży ruch, z czym często mają do czynienia takie procedury. Może to pomóc instrument kodu, który wywołuje metodę wydania macierzystego, w celu przechwycenia tożsamości wywołującego lub ewentualnie śledzenia pełnego stosu i wartość dojścia zwalnianego.  Wartość dojścia można porównać z wartością zgłoszoną przez to NARZĘDZIE MDA.  
  
- Należy zauważyć, że niektóre typy uchwytów natywnych, takich `CloseHandle` jak wszystkie uchwyty Win32, które mogą być zwolnione za pośrednictwem funkcji, współużytkują ten sam obszar nazw uchwytu. Błędne zwolnienie jednego typu uchwytu może powodować problemy z innym. Na przykład przypadkowe zamknięcie uchwytu zdarzenia Win32 dwukrotnie może prowadzić do pozornie niepowiązanego dojścia pliku jest zamykany przedwcześnie. Dzieje się tak, gdy dojście jest zwalniany i wartość dojścia staje się dostępna do użycia do śledzenia innego zasobu, potencjalnie innego typu. Jeśli tak się stanie, a następuje błędne drugie wydanie, dojście niepowiązanych wątku może zostać unieważniony.  
  
## <a name="effect-on-the-runtime"></a>Wpływ na czas działania  
 To MDA nie ma wpływu na CLR.  
  
## <a name="output"></a>Dane wyjściowe  
 Komunikat wskazujący, <xref:System.Runtime.InteropServices.SafeHandle> że <xref:System.Runtime.InteropServices.CriticalHandle> lub nie udało się poprawnie zwolnić dojście. Przykład:  
  
```output
"A SafeHandle or CriticalHandle of type 'MyBrokenSafeHandle'
failed to properly release the handle with value 0x0000BEEF. This
usually indicates that the handle was released incorrectly via
another means (such as extracting the handle using DangerousGetHandle
and closing it directly or building another SafeHandle around it."  
```  
  
## <a name="configuration"></a>Konfigurowanie  
  
```xml  
<mdaConfig>  
  <assistants>  
    <releaseHandleFailed/>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="example"></a>Przykład  
 Poniżej przedstawiono przykład kodu, `releaseHandleFailed` który można aktywować MDA.  
  
```csharp
bool ReleaseHandle()  
{  
    // Calling the Win32 CloseHandle function to release the
    // native handle wrapped by this SafeHandle. This method returns
    // false on failure, but should only fail if the input is invalid
    // (which should not happen here). The method specifically must not
    // fail simply because of lack of resources or other transient
    // failures beyond the user’s control. That would make it unacceptable
    // to call CloseHandle as part of the implementation of this method.  
    return CloseHandle(handle);  
}  
```  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [Diagnozowanie błędów przy użyciu asystentów zarządzanego debugowania](diagnosing-errors-with-managed-debugging-assistants.md)
- [Organizowanie międzyoperacyjne](../interop/interop-marshaling.md)
