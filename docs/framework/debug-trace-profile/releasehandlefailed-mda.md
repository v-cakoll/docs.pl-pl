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
ms.openlocfilehash: 41f6b67ff63d096cc1fa2c599abb06c9c1129952
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2019
ms.locfileid: "71052310"
---
# <a name="releasehandlefailed-mda"></a>releaseHandleFailed MDA
Asystent `releaseHandleFailed` debugowania zarządzanego (MDA) jest aktywowany, aby informować deweloperów, <xref:System.Runtime.InteropServices.SafeHandle.ReleaseHandle%2A> gdy metoda klasy pochodnej <xref:System.Runtime.InteropServices.SafeHandle> lub <xref:System.Runtime.InteropServices.CriticalHandle> zwraca `false`.  
  
## <a name="symptoms"></a>Symptomy  
 Przecieki zasobów lub pamięci.  Jeśli metoda klasy wyprowadza z <xref:System.Runtime.InteropServices.SafeHandle> lub <xref:System.Runtime.InteropServices.CriticalHandle> zakończy się niepowodzeniem, zasób hermetyzowany przez klasę może nie zostać wystawiony lub oczyszczony. <xref:System.Runtime.InteropServices.SafeHandle.ReleaseHandle%2A>  
  
## <a name="cause"></a>Przyczyna  
 Użytkownicy muszą podać implementację <xref:System.Runtime.InteropServices.SafeHandle.ReleaseHandle%2A> metody, jeśli tworzą klasy, które pochodzą z <xref:System.Runtime.InteropServices.SafeHandle> lub <xref:System.Runtime.InteropServices.CriticalHandle>; w takim przypadku okoliczności są specyficzne dla poszczególnych zasobów. Wymagania są jednak następujące:  
  
- <xref:System.Runtime.InteropServices.SafeHandle>i <xref:System.Runtime.InteropServices.CriticalHandle> typy reprezentują otoki wokół ważnych zasobów procesów. Przeciek pamięci mógłby uniemożliwić korzystanie z tego procesu z upływem czasu.  
  
- Wykonanie <xref:System.Runtime.InteropServices.SafeHandle.ReleaseHandle%2A> funkcji przez metodę nie powiodło się. Gdy proces uzyska taki zasób, <xref:System.Runtime.InteropServices.SafeHandle.ReleaseHandle%2A> jest jedynym sposobem jego zwolnienia. W związku z tym niepowodzenie oznacza przecieki zasobów.  
  
- Wszelkie błędy, które wystąpią w trakcie wykonywania <xref:System.Runtime.InteropServices.SafeHandle.ReleaseHandle%2A>, utrudniają wydanie zasobu, są usterką w implementacji <xref:System.Runtime.InteropServices.SafeHandle.ReleaseHandle%2A> samej metody. Jest odpowiedzialny programista, aby upewnić się, że kontrakt jest spełniony, nawet jeśli ten kod wywołuje kod utworzony przez kogoś innego do wykonywania swojej funkcji.  
  
## <a name="resolution"></a>Rozwiązanie  
 Kod używający określonego <xref:System.Runtime.InteropServices.SafeHandle> typu (lub <xref:System.Runtime.InteropServices.CriticalHandle>), który wywołał powiadomienie MDA, powinien zostać sprawdzony, szukając miejsc, w których <xref:System.Runtime.InteropServices.SafeHandle> wartość pierwotnego dojścia jest wyodrębniana z i kopiowana w innym miejscu. Jest to typowa przyczyna błędów w ramach <xref:System.Runtime.InteropServices.SafeHandle> lub <xref:System.Runtime.InteropServices.CriticalHandle> implementacji, ponieważ użycie nieprzetworzonej wartości nie jest już śledzone przez środowisko uruchomieniowe. Jeśli kopia nieprzetworzonego dojścia zostanie ZAMKNIĘTA, może to spowodować, <xref:System.Runtime.InteropServices.SafeHandle.ReleaseHandle%2A> że późniejsze wywołanie zakończyło się niepowodzeniem, ponieważ próba zamknięcia w tym samym dojściem jest nieprawidłowa.  
  
 Istnieje kilka sposobów, w których może wystąpić nieprawidłowe duplikowanie obsługi:  
  
- Wyszukaj wywołania <xref:System.Runtime.InteropServices.SafeHandle.DangerousGetHandle%2A> metody. Wywołania tej metody powinny być przewyższane sporadycznie, a wszystkie znalezione należy ująć w wywołania <xref:System.Runtime.InteropServices.SafeHandle.DangerousAddRef%2A> metod i. <xref:System.Runtime.InteropServices.SafeHandle.DangerousRelease%2A> Te ostatnie metody określają region kodu, w którym wartość nieprzetworzonego dojścia może być bezpiecznie używana. Poza tym regionem lub jeśli liczba odwołań nigdy nie rośnie w pierwszym miejscu, wartość dojścia może być unieważniona w dowolnym momencie przez wywołanie do <xref:System.Runtime.InteropServices.SafeHandle.Dispose%2A> lub <xref:System.Runtime.InteropServices.SafeHandle.Close%2A> w innym wątku. Gdy wszystkie zastosowania <xref:System.Runtime.InteropServices.SafeHandle.DangerousGetHandle%2A> zostały śledzone w dół, należy postępować zgodnie z ścieżką, aby zapewnić, że nie zostanie ona przekazana do jakiegoś składnika, który ostatecznie wywoła `CloseHandle` lub inną metodę natywną niskiego poziomu, która zwolni uchwyt.  
  
- Upewnij się, że kod, który jest używany do <xref:System.Runtime.InteropServices.SafeHandle> inicjowania z prawidłową wartością nieprzetworzonego dojścia, jest właścicielem dojścia. Jeśli zostanie <xref:System.Runtime.InteropServices.SafeHandle> utworzona wokół uchwytu, kod nie jest właścicielem bez `ownsHandle` ustawienia parametru do `false` <xref:System.Runtime.InteropServices.SafeHandle> w konstruktorze podstawowym, a zarówno, jak i właściciel rzeczywistego uchwytu, może próbować zamknąć dojście, prowadząc do błędu w <xref:System.Runtime.InteropServices.SafeHandle.ReleaseHandle%2A> Jeśli utracirasę.<xref:System.Runtime.InteropServices.SafeHandle>  
  
- Gdy jest zorganizowany między domenami aplikacji, upewnij się, <xref:System.Runtime.InteropServices.SafeHandle> że wyprowadzenie wyprowadzania zostało oznaczone jako możliwe do serializacji. <xref:System.Runtime.InteropServices.SafeHandle> W rzadkich przypadkach, gdy Klasa pochodna <xref:System.Runtime.InteropServices.SafeHandle> została przeprowadzona do serializacji, należy <xref:System.Runtime.Serialization.ISerializable> zaimplementować interfejs lub użyć jednej z innych technik do ręcznego sterowania procesem serializacji i deserializacji. Jest to wymagane, ponieważ domyślna akcja serializacji polega na utworzeniu bitowego klonu załączonej nieprzetworzonej wartości, co spowoduje <xref:System.Runtime.InteropServices.SafeHandle> , że dwa wystąpienia zauważają, że są właścicielami tego samego uchwytu. Oba będą podejmować próby wywołania <xref:System.Runtime.InteropServices.SafeHandle.ReleaseHandle%2A> w ramach tego samego uchwytu w pewnym momencie. Druga <xref:System.Runtime.InteropServices.SafeHandle> w tym celu zakończy się niepowodzeniem. Prawidłowym sposobem działania podczas serializowania <xref:System.Runtime.InteropServices.SafeHandle> jest `DuplicateHandle` wywołanie funkcji lub podobnej funkcji dla typu uchwytu natywnego w celu dokonania odrębnej kopii dojścia prawnego. Jeśli typ uchwytu nie obsługuje tego typu, <xref:System.Runtime.InteropServices.SafeHandle> nie można go serializować.  
  
- Może być możliwe śledzenie, gdzie dojście jest wczesnie zamykane, co prowadzi do błędu, gdy <xref:System.Runtime.InteropServices.SafeHandle.ReleaseHandle%2A> Metoda jest ostatecznie wywoływana, przez umieszczenie punktu przerwania debugera w procedurze natywnej używanej do zwolnienia dojścia, na `CloseHandle` przykład funkcji. Może to nie być możliwe w przypadku scenariuszy obciążeniowych, a nawet średnich testów funkcjonalnych spowodowanych dużym ruchem, które często omawiają te procedury. Może ona ułatwić instrumentację kodu, który wywołuje natywną metodę wydania, aby przechwycić tożsamość obiektu wywołującego lub być może pełny ślad stosu i wartość zwalnianego dojścia.  Wartość dojścia można porównać z wartością raportowaną przez to zdarzenie MDA.  
  
- Należy zauważyć, że niektóre typy uchwytów natywnych, takie jak wszystkie uchwyty Win32, które mogą `CloseHandle` być uwalniane za pośrednictwem funkcji, współdzielą tę samą przestrzeń nazw uchwytu. Błędne wydanie jednego typu dojścia może spowodować problemy z innym. Na przykład przypadkowe zamknięcie dojścia zdarzenia Win32 dwa razy może prowadzić do przedwczesnego zamknięcia niepowiązanego dojścia do pliku. Dzieje się tak, gdy dojście zostanie wydane, a wartość uchwytu będzie dostępna do śledzenia innego zasobu, a potencjalnie innego typu. W takim przypadku i następuje błędne drugie wydanie, dojście niepowiązanego wątku może być unieważnione.  
  
## <a name="effect-on-the-runtime"></a>Wpływ na środowisko uruchomieniowe  
 To zdarzenie MDA nie ma wpływu na środowisko CLR.  
  
## <a name="output"></a>Dane wyjściowe  
 Komunikat informujący o tym <xref:System.Runtime.InteropServices.SafeHandle> , że <xref:System.Runtime.InteropServices.CriticalHandle> lub nie powiodło się prawidłowe wydanie dojścia. Przykład:  
  
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
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [Diagnozowanie błędów przy użyciu asystentów zarządzanego debugowania](diagnosing-errors-with-managed-debugging-assistants.md)
- [Marshaling międzyoperacyjny](../interop/interop-marshaling.md)
