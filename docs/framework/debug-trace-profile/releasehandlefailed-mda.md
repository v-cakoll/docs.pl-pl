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
ms.openlocfilehash: 265344cb100a41cde5443cd0914dc66271aabf93
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/14/2020
ms.locfileid: "77216112"
---
# <a name="releasehandlefailed-mda"></a>releaseHandleFailed MDA
`releaseHandleFailed` zarządzanego asystenta debugowania (MDA) polega na powiadamianiu deweloperów, gdy metoda <xref:System.Runtime.InteropServices.SafeHandle.ReleaseHandle%2A> klasy pochodnej <xref:System.Runtime.InteropServices.SafeHandle> lub <xref:System.Runtime.InteropServices.CriticalHandle> zwraca `false`.  
  
## <a name="symptoms"></a>Objawy  
 Przecieki zasobów lub pamięci.  Jeśli metoda <xref:System.Runtime.InteropServices.SafeHandle.ReleaseHandle%2A> klasy pochodzącej od <xref:System.Runtime.InteropServices.SafeHandle> lub <xref:System.Runtime.InteropServices.CriticalHandle> kończy się niepowodzeniem, zasób hermetyzowany przez klasę może nie zostać wystawiony lub oczyszczony.  
  
## <a name="cause"></a>Przyczyna  
 Użytkownicy muszą podać implementację metody <xref:System.Runtime.InteropServices.SafeHandle.ReleaseHandle%2A>, jeśli tworzą klasy, które pochodzą od <xref:System.Runtime.InteropServices.SafeHandle> lub <xref:System.Runtime.InteropServices.CriticalHandle>; z tego względu okoliczności są specyficzne dla poszczególnych zasobów. Wymagania są jednak następujące:  
  
- typy <xref:System.Runtime.InteropServices.SafeHandle> i <xref:System.Runtime.InteropServices.CriticalHandle> reprezentują otoki wokół ważnych zasobów procesów. Przeciek pamięci mógłby uniemożliwić korzystanie z tego procesu z upływem czasu.  
  
- Metoda <xref:System.Runtime.InteropServices.SafeHandle.ReleaseHandle%2A> nie może wykonać tej funkcji. Gdy proces uzyska taki zasób, <xref:System.Runtime.InteropServices.SafeHandle.ReleaseHandle%2A> jest jedynym sposobem jego zwolnienia. W związku z tym niepowodzenie oznacza przecieki zasobów.  
  
- Wszelkie błędy, które wystąpią podczas wykonywania <xref:System.Runtime.InteropServices.SafeHandle.ReleaseHandle%2A>, utrudniają wydanie zasobu, są usterką w implementacji samej metody <xref:System.Runtime.InteropServices.SafeHandle.ReleaseHandle%2A>. Jest odpowiedzialny programista, aby upewnić się, że kontrakt jest spełniony, nawet jeśli ten kod wywołuje kod utworzony przez kogoś innego do wykonywania swojej funkcji.  
  
## <a name="resolution"></a>Rozwiązanie  
 Kod, który używa określonego typu <xref:System.Runtime.InteropServices.SafeHandle> (lub <xref:System.Runtime.InteropServices.CriticalHandle>), który wywołał powiadomienie MDA, powinien zostać sprawdzony, szukając miejsc, w których wartość pierwotnego dojścia jest wyodrębniana z <xref:System.Runtime.InteropServices.SafeHandle> i kopiowana w innym miejscu. Jest to typowa przyczyna błędów w ramach implementacji <xref:System.Runtime.InteropServices.SafeHandle> lub <xref:System.Runtime.InteropServices.CriticalHandle>, ponieważ użycie nieprzetworzonej wartości nie jest już śledzone przez środowisko uruchomieniowe. Jeśli kopia nieprzetworzonych dojść zostanie ZAMKNIĘTA, może to spowodować, że późniejsze <xref:System.Runtime.InteropServices.SafeHandle.ReleaseHandle%2A> wywołanie zakończyło się niepowodzeniem, ponieważ próba zamknięcia w tym samym dojściem jest nieprawidłowa.  
  
 Istnieje kilka sposobów, w których może wystąpić nieprawidłowe duplikowanie obsługi:  
  
- Poszukaj wywołań metody <xref:System.Runtime.InteropServices.SafeHandle.DangerousGetHandle%2A>. Wywołania tej metody powinny być przewyższane sporadycznie, a wszystkie znalezione należy ująć w wywołania metod <xref:System.Runtime.InteropServices.SafeHandle.DangerousAddRef%2A> i <xref:System.Runtime.InteropServices.SafeHandle.DangerousRelease%2A>. Te ostatnie metody określają region kodu, w którym wartość nieprzetworzonego dojścia może być bezpiecznie używana. Poza tym regionem lub jeśli liczba odwołań nigdy nie rośnie w pierwszym miejscu, wartość dojścia może być unieważniona w dowolnym momencie przez wywołanie do <xref:System.Runtime.InteropServices.SafeHandle.Dispose%2A> lub <xref:System.Runtime.InteropServices.SafeHandle.Close%2A> w innym wątku. Gdy wszystkie zastosowania <xref:System.Runtime.InteropServices.SafeHandle.DangerousGetHandle%2A> zostały śledzone, należy postępować zgodnie z ścieżką, która jest wykonywana przez nieprzetworzony uchwyt, aby upewnić się, że nie jest on przekazywany do jakiegoś składnika, który ostatecznie wywoła `CloseHandle` lub inną metodę natywną niskiego poziomu, która zwolni uchwyt.  
  
- Upewnij się, że kod, który jest używany do inicjowania <xref:System.Runtime.InteropServices.SafeHandle> z prawidłową wartością nieprzetworzonego dojścia, jest właścicielem dojścia. W przypadku tworzenia <xref:System.Runtime.InteropServices.SafeHandle> wokół uchwytu kod nie jest właścicielem bez ustawienia parametru `ownsHandle` do `false` w konstruktorze podstawowym, a następnie zarówno <xref:System.Runtime.InteropServices.SafeHandle>, jak i właściciel rzeczywistego uchwytu mogą próbować zamknąć uchwyt, prowadząc do błędu w <xref:System.Runtime.InteropServices.SafeHandle.ReleaseHandle%2A>, jeśli <xref:System.Runtime.InteropServices.SafeHandle> utraci rasę.  
  
- Gdy <xref:System.Runtime.InteropServices.SafeHandle> jest zorganizowany między domenami aplikacji, upewnij się, że używane dane pochodne <xref:System.Runtime.InteropServices.SafeHandle> zostały oznaczone jako możliwe do serializacji. W rzadkich przypadkach, gdy Klasa pochodna <xref:System.Runtime.InteropServices.SafeHandle> została przeprowadzona do serializacji, należy zaimplementować interfejs <xref:System.Runtime.Serialization.ISerializable> lub użyć jednej z innych technik do ręcznego sterowania procesem serializacji i deserializacji. Jest to wymagane, ponieważ domyślna akcja serializacji polega na utworzeniu bitowego klonu pozostałej nieprzetworzonej wartości dojścia, co spowoduje, że dwa <xref:System.Runtime.InteropServices.SafeHandle> wystąpienia zastanawiają się, że są one własnością tego samego uchwytu. Oba będą podejmować próby wywołania <xref:System.Runtime.InteropServices.SafeHandle.ReleaseHandle%2A> w ramach tego samego uchwytu w pewnym momencie. Druga <xref:System.Runtime.InteropServices.SafeHandle>, aby to zrobić, zakończy się niepowodzeniem. Prawidłowym sposobem działania podczas serializowania <xref:System.Runtime.InteropServices.SafeHandle> jest wywołanie funkcji `DuplicateHandle` lub podobnej funkcji dla typu uchwytu natywnego w celu dokonania odrębnej kopii dojścia prawnego. Jeśli typ uchwytu nie obsługuje tego typu, <xref:System.Runtime.InteropServices.SafeHandle> zawijania, nie można go serializować.  
  
- Może być możliwe śledzenie miejsca, w którym dojście jest zamykane wcześnie, co prowadzi do błędu, gdy metoda <xref:System.Runtime.InteropServices.SafeHandle.ReleaseHandle%2A> jest ostatecznie wywoływana, przez umieszczenie punktu przerwania debugera w procedurze natywnej używanej do zwolnienia dojścia, na przykład funkcji `CloseHandle`. Może to nie być możliwe w przypadku scenariuszy obciążeniowych, a nawet średnich testów funkcjonalnych spowodowanych dużym ruchem, które często omawiają te procedury. Może ona ułatwić instrumentację kodu, który wywołuje natywną metodę wydania, aby przechwycić tożsamość obiektu wywołującego lub być może pełny ślad stosu i wartość zwalnianego dojścia.  Wartość dojścia można porównać z wartością raportowaną przez to zdarzenie MDA.  
  
- Należy zauważyć, że niektóre typy uchwytów natywnych, takie jak wszystkie uchwyty Win32, które mogą być wydane za pośrednictwem funkcji `CloseHandle`, współdzielą tę samą przestrzeń nazw uchwytu. Błędne wydanie jednego typu dojścia może spowodować problemy z innym. Na przykład przypadkowe zamknięcie dojścia zdarzenia Win32 dwa razy może prowadzić do przedwczesnego zamknięcia niepowiązanego dojścia do pliku. Dzieje się tak, gdy dojście zostanie wydane, a wartość uchwytu będzie dostępna do śledzenia innego zasobu, a potencjalnie innego typu. W takim przypadku i następuje błędne drugie wydanie, dojście niepowiązanego wątku może być unieważnione.  
  
## <a name="effect-on-the-runtime"></a>Wpływ na środowisko uruchomieniowe  
 To zdarzenie MDA nie ma wpływu na środowisko CLR.  
  
## <a name="output"></a>Dane wyjściowe  
 Komunikat informujący o tym, że <xref:System.Runtime.InteropServices.SafeHandle> lub <xref:System.Runtime.InteropServices.CriticalHandle> nie powiodło się prawidłowe wydanie dojścia. Na przykład:  
  
```output
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
 Poniżej znajduje się przykładowy kod, który umożliwia aktywowanie `releaseHandleFailed` MDA.  
  
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
- [Marshaling międzyoperacyjny](../interop/interop-marshaling.md)
