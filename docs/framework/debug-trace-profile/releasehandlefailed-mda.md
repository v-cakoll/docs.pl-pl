---
title: releaseHandleFailed MDA
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- managed debugging assistants (MDAs), handles
- release handle failed
- CriticalHandle class, run-time errors
- releaseHandleFailed MDA
- ReleaseHandle method
- SafeHandle class, run-time errors
- MDAs (managed debugging assistants), handles
ms.assetid: 44cd98ba-95e5-40a1-874d-e8e163612c51
caps.latest.revision: "14"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: cbd6e2a52eb576f321dfa7dda5682d325f554158
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="releasehandlefailed-mda"></a>releaseHandleFailed MDA
`releaseHandleFailed` Zarządzanego debugowania (MDA) Asystenta jest aktywowany jest powiadomiono deweloperzy podczas <xref:System.Runtime.InteropServices.SafeHandle.ReleaseHandle%2A> metoda klasy pochodzące z <xref:System.Runtime.InteropServices.SafeHandle> lub <xref:System.Runtime.InteropServices.CriticalHandle> zwraca `false`.  
  
## <a name="symptoms"></a>Symptomy  
 Przecieki pamięci lub zasobów.  Jeśli <xref:System.Runtime.InteropServices.SafeHandle.ReleaseHandle%2A> metody klasy wywodzące się z <xref:System.Runtime.InteropServices.SafeHandle> lub <xref:System.Runtime.InteropServices.CriticalHandle> nie powiedzie się, a następnie zasobów hermetyzowany przez klasę może nie zostały wydane lub wyczyścić.  
  
## <a name="cause"></a>Przyczyna  
 Użytkownik musi podać wykonania <xref:System.Runtime.InteropServices.SafeHandle.ReleaseHandle%2A> metodę, jeśli tworzą klasy, która pochodzi z <xref:System.Runtime.InteropServices.SafeHandle> lub <xref:System.Runtime.InteropServices.CriticalHandle>; w związku z tym okoliczności są specyficzne dla poszczególnych zasobów. Jednak wymagania są następujące:  
  
-   <xref:System.Runtime.InteropServices.SafeHandle>i <xref:System.Runtime.InteropServices.CriticalHandle> typy reprezentują otoki wokół procesu ważnych zasobów. Przeciek pamięci spowodowałoby procesu nie można użyć w czasie.  
  
-   <xref:System.Runtime.InteropServices.SafeHandle.ReleaseHandle%2A> — Metoda nie zakończyć się niepowodzeniem do realizacji funkcji. Po proces uzyskuje taki zasób <xref:System.Runtime.InteropServices.SafeHandle.ReleaseHandle%2A> jest jedynym sposobem na jego wersji. W związku z tym Niepowodzenie oznacza przecieków zasobów.  
  
-   Jakiekolwiek niepowodzenie, która występuje podczas wykonywania <xref:System.Runtime.InteropServices.SafeHandle.ReleaseHandle%2A>utrudnienia wersji zasobu, jest to błąd w implementacji <xref:System.Runtime.InteropServices.SafeHandle.ReleaseHandle%2A> metody. Jest odpowiedzialny za programisty, aby upewnić się, że kontrakt jest spełnione, nawet jeśli ten kod wywołuje kod utworzone przez innego użytkownika do realizacji funkcji.  
  
## <a name="resolution"></a>Rozwiązanie  
 Kod, który korzysta z konkretnym <xref:System.Runtime.InteropServices.SafeHandle> (lub <xref:System.Runtime.InteropServices.CriticalHandle>) typu, który uruchamiany powiadomień MDA należy ją sprawdzić, wyszukiwanie miejsca, w którym wartość Nieprzetworzona dojścia jest wyodrębniana z <xref:System.Runtime.InteropServices.SafeHandle> i skopiowany do innej lokalizacji. Jest to zwykle przyczynę awarii w <xref:System.Runtime.InteropServices.SafeHandle> lub <xref:System.Runtime.InteropServices.CriticalHandle> implementacji, ponieważ użycie wartości nieprzetworzonej dojścia następnie nie jest już śledzona przez środowisko uruchomieniowe. Kopiowania raw dojścia później zostanie zamknięty, może spowodować nowszego <xref:System.Runtime.InteropServices.SafeHandle.ReleaseHandle%2A> wywołanie kończy się niepowodzeniem, ponieważ próba zamknięcia zostanie podjęta na tej samej uchwytu, który teraz jest nieprawidłowy.  
  
 Istnieją różne sposoby, w którym mogą występować duplikatów nieprawidłowe dojście:  
  
-   Wyszukaj wywołań <xref:System.Runtime.InteropServices.SafeHandle.DangerousGetHandle%2A> metody. Wywołania tej metody powinna być nadmiernie rzadkich i które możesz znaleźć powinny być ujęte wywołań <xref:System.Runtime.InteropServices.SafeHandle.DangerousAddRef%2A> i <xref:System.Runtime.InteropServices.SafeHandle.DangerousRelease%2A> metody. Te metody ostatnie Określ region kodu, w którym wartość Nieprzetworzona dojścia może być już używany. Poza tym regionie lub jeśli liczba odwołań nigdy nie jest zwiększany w pierwszej kolejności, wartość uchwytu może unieważnionych w dowolnym momencie przez wywołanie do <xref:System.Runtime.InteropServices.SafeHandle.Dispose%2A> lub <xref:System.Runtime.InteropServices.SafeHandle.Close%2A> w innym wątku. Raz wszystkich zastosowań <xref:System.Runtime.InteropServices.SafeHandle.DangerousGetHandle%2A> były śledzone w dół, należy wykonać, ścieżka raw dojście przyjmuje aby upewnić się, nie zostanie przekazany dalej do niektórych składnika, który ostatecznie wywoła `CloseHandle` lub innej metody natywnej niskiego poziomu spowoduje zwolnienie uchwytu.  
  
-   Upewnij się, że kod, który służy do inicjowania <xref:System.Runtime.InteropServices.SafeHandle> z prawidłowym dojściem nieprzetworzone wartości jest właścicielem dojście. Jeśli możesz tworzyć <xref:System.Runtime.InteropServices.SafeHandle> wokół dojścia kodu nie jest właścicielem bez ustawienia `ownsHandle` parametr `false` w konstruktora podstawowego, a następnie zarówno <xref:System.Runtime.InteropServices.SafeHandle> i właściciela dojścia rzeczywistych można spróbować zamknąć uchwytu, co może prowadzić do błędu w <xref:System.Runtime.InteropServices.SafeHandle.ReleaseHandle%2A> Jeśli <xref:System.Runtime.InteropServices.SafeHandle> utraci wyścigu.  
  
-   Gdy <xref:System.Runtime.InteropServices.SafeHandle> jest przekazywane między domenami aplikacji, upewnij się, <xref:System.Runtime.InteropServices.SafeHandle> pochodnym używany został oznaczony jako możliwy do serializacji. W rzadkich przypadkach, gdy klasa pochodzi od <xref:System.Runtime.InteropServices.SafeHandle> zostało wprowadzone do serializacji, powinien implementować <xref:System.Runtime.Serialization.ISerializable> interfejsu lub użyj jednego z innych technik dla kontrolowanie serializacji i deserializacji proces ręcznie. Jest to wymagane, ponieważ domyślnym działaniem serializacji jest tworzenie własnego klonu bitowe wartości objętego dojścia raw, co w dwóch <xref:System.Runtime.InteropServices.SafeHandle> myśląc właścicielem tego samego dojście wystąpienia. Zarówno będzie próbował wywołać <xref:System.Runtime.InteropServices.SafeHandle.ReleaseHandle%2A> na tym samym dojście w pewnym momencie. Drugi <xref:System.Runtime.InteropServices.SafeHandle> w tym celu zakończy się niepowodzeniem. Prawidłowy sposób działania podczas serializowania <xref:System.Runtime.InteropServices.SafeHandle> jest wywołanie `DuplicateHandle` funkcji lub podobnych funkcji dla urządzenia natywnego obsługiwać typ do skopiowania różne dojścia prawnych. Jeśli nie obsługuje danego typu uchwytu, a następnie <xref:System.Runtime.InteropServices.SafeHandle> zawijania jej typ jest niemożliwe do serializacji.  
  
-   Może być możliwe do śledzenia, gdy uchwyt zostaje zamknięte wcześnie, co może prowadzić do awarii podczas <xref:System.Runtime.InteropServices.SafeHandle.ReleaseHandle%2A> koniec jest wywoływana metoda, przez umieszczenie punktu przerwania debugera na procedury macierzystym, przy użyciu dojścia, na przykład `CloseHandle` funkcji. To nie być możliwe scenariusze akcent lub nawet średnich testy funkcjonalne z powodu dużego ruchu takie procedury często postępowania w przypadku. Warto Instrumentacja kod, który wywołuje metody natywnej wersji w celu przechwytywania tożsamości wywołującego, lub prawdopodobnie ślad stosu pełne, a wartość uchwytu został wydany.  Wartość uchwytu może zostać porównane z wartość zgłaszaną przez to zdarzenie MDA.  
  
-   Należy pamiętać, że niektóre typy uchwyt macierzysty, takie jak wszystkie Win32 obsługuje będą dostępne za pośrednictwem `CloseHandle` funkcji, udostępnianie tego samego obszaru nazw dojścia. Błędne wersji — typ uchwytu co może spowodować problemy z inną. Na przykład przypadkowo dwukrotnie zamykania obsługi zdarzenia Win32 może prowadzić do dojście do pliku najwyraźniej niepowiązanych przedwcześnie zamknięte. Dzieje się tak po zwolnieniu dojście i wartość dojścia staje się dostępna do użycia, śledzić inny zasób potencjalnie innego typu. Jeśli to się stanie, następuje błędne drugie wydanie dojście wątku niepowiązanych może unieważniona.  
  
## <a name="effect-on-the-runtime"></a>Wpływ na środowisko uruchomieniowe  
 To zdarzenie MDA nie ma wpływu na środowisko CLR.  
  
## <a name="output"></a>Dane wyjściowe  
 Komunikat wskazujący, że <xref:System.Runtime.InteropServices.SafeHandle> lub <xref:System.Runtime.InteropServices.CriticalHandle> zdołał poprawnie zwolnić dojścia. Na przykład:  
  
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
 Poniżej przedstawiono przykładowy kod, który można aktywować `releaseHandleFailed` MDA.  
  
```  
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
 <xref:System.Runtime.InteropServices.MarshalAsAttribute>  
 [Diagnozowanie błędów przy użyciu Asystenci zarządzanego debugowania](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)  
 [Przekazywanie międzyoperacyjne](../../../docs/framework/interop/interop-marshaling.md)
