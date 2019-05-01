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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 3b149a9b8ee41f5e196fd69258044f9b6563cb99
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61874006"
---
# <a name="releasehandlefailed-mda"></a>releaseHandleFailed MDA
`releaseHandleFailed` Zarządzanego debugowania (MDA) Asystenta aktywacji jest do powiadamiania deweloperów podczas <xref:System.Runtime.InteropServices.SafeHandle.ReleaseHandle%2A> metoda klasę pochodną <xref:System.Runtime.InteropServices.SafeHandle> lub <xref:System.Runtime.InteropServices.CriticalHandle> zwraca `false`.  
  
## <a name="symptoms"></a>Symptomy  
 Przeciek zasobu lub pamięci.  Jeśli <xref:System.Runtime.InteropServices.SafeHandle.ReleaseHandle%2A> metody pochodząca od klasy <xref:System.Runtime.InteropServices.SafeHandle> lub <xref:System.Runtime.InteropServices.CriticalHandle> zakończy się niepowodzeniem, a następnie zasobów hermetyzowane w klasie może nie zostały wydane lub oczyszczone.  
  
## <a name="cause"></a>Przyczyna  
 Użytkownik musi podać implementacja <xref:System.Runtime.InteropServices.SafeHandle.ReleaseHandle%2A> metodę, jeśli tworzą klasy, która pochodzi od <xref:System.Runtime.InteropServices.SafeHandle> lub <xref:System.Runtime.InteropServices.CriticalHandle>; w związku z tym okoliczności są specyficzne dla poszczególnych zasobów. Jednak wymagania są następujące:  
  
- <xref:System.Runtime.InteropServices.SafeHandle> i <xref:System.Runtime.InteropServices.CriticalHandle> typy reprezentują otok wokół procesu ważnych zasobów. Przeciek pamięci może uniemożliwić proces korzystanie z tej wraz z upływem czasu.  
  
- <xref:System.Runtime.InteropServices.SafeHandle.ReleaseHandle%2A> Metody nie zakończyć się niepowodzeniem do realizacji funkcji. Gdy proces uzyskuje jakiś zasób, <xref:System.Runtime.InteropServices.SafeHandle.ReleaseHandle%2A> jest jedynym sposobem jej wersji. W związku z tym Niepowodzenie oznacza przeciekom zasobów.  
  
- Jakiekolwiek niepowodzenie, które występują podczas wykonywania <xref:System.Runtime.InteropServices.SafeHandle.ReleaseHandle%2A>referują wersji zasobu, jest to błąd w implementacji <xref:System.Runtime.InteropServices.SafeHandle.ReleaseHandle%2A> sama metoda. Jest odpowiedzialny za programisty, zapewnienie, że Umowa jest spełniony, nawet wtedy, gdy kod wywołuje kod utworzony przez inną osobę do realizacji funkcji.  
  
## <a name="resolution"></a>Rozwiązanie  
 Kod, który używa określonego <xref:System.Runtime.InteropServices.SafeHandle> (lub <xref:System.Runtime.InteropServices.CriticalHandle>) typ, który spowodował zgłoszenie MDA powinna zostać przejrzana pod, szukasz miejsca, w którym wartość dojścia pierwotne są wyodrębniane z <xref:System.Runtime.InteropServices.SafeHandle> i kopiowane w innym miejscu. To jest Najczęstszą przyczyną błędów w ramach <xref:System.Runtime.InteropServices.SafeHandle> lub <xref:System.Runtime.InteropServices.CriticalHandle> implementacji, ponieważ użycie wartości pierwotnych uchwyt następnie nie jest już śledzony przez środowisko uruchomieniowe. Jeśli kopiowania pierwotne uchwyt później zostanie zamknięty, może to spowodować później <xref:System.Runtime.InteropServices.SafeHandle.ReleaseHandle%2A> wywołanie się nie powieść, ponieważ zamknięcia zostanie podjęta na tym samym uchwyt, który teraz jest nieprawidłowy.  
  
 Istnieją różne sposoby, w których może wystąpić duplikacja dojścia niepoprawne:  
  
- Poszukaj wywołania <xref:System.Runtime.InteropServices.SafeHandle.DangerousGetHandle%2A> metody. Wywołania tej metody powinna być nadmiernie rzadkich i tych, które można znaleźć powinny być otoczona wywołania <xref:System.Runtime.InteropServices.SafeHandle.DangerousAddRef%2A> i <xref:System.Runtime.InteropServices.SafeHandle.DangerousRelease%2A> metody. Metody te ostatnie określić region kodu, w którym wartość dojścia pierwotnych może być już używany. Poza tym regionem lub jeśli licznik odwołań nigdy nie jest zwiększany w pierwszej kolejności, wartość dojścia unieważnić w dowolnym momencie przez wywołanie <xref:System.Runtime.InteropServices.SafeHandle.Dispose%2A> lub <xref:System.Runtime.InteropServices.SafeHandle.Close%2A> w innym wątku. Gdy wszystkie przypadki użycia <xref:System.Runtime.InteropServices.SafeHandle.DangerousGetHandle%2A> były śledzone w dół, należy przestrzegać ścieżki pierwotne uchwyt trwa upewnij się, nie zostanie przekazany dalej do niektórych składnika, który będzie wybierany po pewnym czasie `CloseHandle` lub innej metody natywnej niskiego poziomu spowoduje zwolnienie uchwytu.  
  
- Upewnij się, że kod, który służy do inicjowania <xref:System.Runtime.InteropServices.SafeHandle> przy użyciu prawidłowego uchwytu pierwotne wartości jest właścicielem uchwytu. Jeśli możesz tworzą <xref:System.Runtime.InteropServices.SafeHandle> wokół uchwyt kodu nie jest właścicielem bez ustawienia `ownsHandle` parametr `false` w konstruktora bazowego, a następnie obie <xref:System.Runtime.InteropServices.SafeHandle> i właściciel uchwytu rzeczywistych spróbować zamknąć dojście, co prowadzi do błędu w <xref:System.Runtime.InteropServices.SafeHandle.ReleaseHandle%2A> Jeśli <xref:System.Runtime.InteropServices.SafeHandle> traci problemu wyścigu.  
  
- Gdy <xref:System.Runtime.InteropServices.SafeHandle> jest przekazywane między domenami aplikacji, upewnij się, <xref:System.Runtime.InteropServices.SafeHandle> pochodnym używany został oznaczony jako możliwy do serializacji. W rzadkich przypadkach, której klasą pochodną <xref:System.Runtime.InteropServices.SafeHandle> zostało wprowadzone do serializacji, należy zaimplementować <xref:System.Runtime.Serialization.ISerializable> interfejs lub użyj jednego z innych technik do sterowania serializacji i deserializacji proces ręcznie. Jest to wymagane, ponieważ domyślnym działaniem serializacji jest tworzenie własnego klonu bitowe wartości ujęty uchwyt raw, co dwa <xref:System.Runtime.InteropServices.SafeHandle> myśl posiadanych dojście do tego samego wystąpienia. Zarówno podejmie próbę wywołania <xref:System.Runtime.InteropServices.SafeHandle.ReleaseHandle%2A> na tym samym dojście w pewnym momencie. Drugi <xref:System.Runtime.InteropServices.SafeHandle> czynność zakończy się niepowodzeniem. Poprawny sposób postępowania podczas serializowania <xref:System.Runtime.InteropServices.SafeHandle> jest wywołanie `DuplicateHandle` funkcji lub podobną funkcję do natywnego obsługi typu umożliwia skopiowanie distinct uchwyt prawnych. Jeśli danego typu dojścia nie obsługuje to a następnie <xref:System.Runtime.InteropServices.SafeHandle> zawijania jego typ nie może zostać wykonana możliwy do serializacji.  
  
- Może być możliwe do śledzenia, gdzie uchwyt jest zamykana wcześnie, co prowadzi do błędu podczas <xref:System.Runtime.InteropServices.SafeHandle.ReleaseHandle%2A> metoda na koniec jest wywoływana przez umieszczenie punktu przerwania debugera na rutynowych natywnych przy użyciu dojścia, na przykład `CloseHandle` funkcji. To nie być możliwe scenariusze obciążenia lub nawet o średniej wielkości testy funkcjonalne ze względu na duży ruch często dotyczy tych procedur. Pomocne może być Instrumentacja kod, który wywołuje metodę natywnej wersji, w celu przechwycenia tożsamość obiektu wywołującego, lub ewentualnie pełen ślad stosu, a wartość dojścia wydany.  Wartość dojścia można porównać z wartość zgłaszaną przez to zdarzenie MDA.  
  
- Należy pamiętać, że niektóre typy uchwyt macierzysty, taką jak system Win32 obsługuje będą dostępne za pośrednictwem `CloseHandle` funkcji, udostępnianie tej samej przestrzeni nazw dojście. Błędne wersję typu określonego dojścia może spowodować problemy z innego. Na przykład przypadkowo dwukrotnie zamyka uchwyt zdarzeń Win32 może prowadzić do dojście do pliku najwyraźniej niepowiązanych przedwcześnie zamknięte. Dzieje się tak, po zwolnieniu dojścia i wartość dojścia staje się dostępna do użycia śledzić inny zasób, potencjalnie innego typu. Jeśli to się dzieje, następuje błędne drugie wydanie może unieważniony dojście wątku niepowiązanych.  
  
## <a name="effect-on-the-runtime"></a>Wpływ na środowisko uruchomieniowe  
 To zdarzenie MDA nie ma wpływu na środowisko CLR.  
  
## <a name="output"></a>Dane wyjściowe  
 Komunikat wskazujący, że <xref:System.Runtime.InteropServices.SafeHandle> lub <xref:System.Runtime.InteropServices.CriticalHandle> nie można zwolnić prawidłowo uchwytu. Na przykład:  
  
```  
"A SafeHandle or CriticalHandle of type 'MyBrokenSafeHandle'   
failed to properly release the handle with value 0x0000BEEF. This   
usually indicates that the handle was released incorrectly via   
another means (such as extracting the handle using DangerousGetHandle   
and closing it directly or building another SafeHandle around it."  
```  
  
## <a name="configuration"></a>Konfiguracja  
  
```xml  
<mdaConfig>  
  <assistants>  
    <releaseHandleFailed/>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="example"></a>Przykład  
 Poniżej przedstawiono przykładowy kod, który może aktywować `releaseHandleFailed` MDA.  
  
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
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [Diagnozowanie błędów przy użyciu asystentów zarządzanego debugowania](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
- [Marshaling międzyoperacyjny](../../../docs/framework/interop/interop-marshaling.md)
