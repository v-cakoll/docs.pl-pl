---
title: Aplikacje wielowątkowe (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 02b0444b-2e68-4f2c-bc28-28c046004017
ms.openlocfilehash: ab4b8d1c77ae75aee6f2cf459258766f88d86abe
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="multithreaded-applications-visual-basic"></a>Aplikacje wielowątkowe (Visual Basic)
Za pomocą Visual Basic mogą pisać aplikacje, służących do wykonywania wielu zadań jednocześnie. Zadania związane z możliwości maksymalnie innych zadań można wykonywać w oddzielnych wątkach proces znany jako *wielowątkowość* lub *wolne wątkowość*.  
  
 Aplikacje korzystające z wielowątkowość są bardziej odpowiednie do wprowadzenia danych przez użytkownika, ponieważ interfejsu użytkownika pozostaje aktywne, jak wykonać zadania obciążenie procesora na poszczególne wątki. Wielowątkowość jest również przydatne podczas tworzenia skalowalnych aplikacji, ponieważ użytkownik może dodać wątków w miarę wzrostu obciążenia.  
  
## <a name="creating-and-using-threads"></a>Tworzenie i używanie wątków  
 Aby uzyskać większą kontrolę nad zachowanie wątków aplikacji, można zarządzać wątki samodzielnie. Jednak należy pamiętać, że zapisywania poprawne wielowątkowe aplikacje mogą być trudne: aplikacja może przestać odpowiadać lub środowisko przejściowe błędy spowodowane wyścigu. Aby uzyskać więcej informacji, zobacz [składniki obsługujące wielowątkowość](http://msdn.microsoft.com/library/4f7c7377-a782-4bd0-aaa3-9db8c12945ee).  
  
 Tworzenie nowego wątku przez deklarowanie zmiennej typu <xref:System.Threading.Thread> i wywołanie konstruktora, podając nazwę procedury lub metodę, która ma być wykonane w nowym wątku. Poniższy kod stanowi przykład.  
  
```vb  
Dim newThread As New System.Threading.Thread(AddressOf AMethod)  
```  
  
### <a name="starting-and-stopping-threads"></a>Uruchamianie i zatrzymywanie wątków  
 Aby rozpocząć wykonywanie nowego wątku, należy użyć <xref:System.Threading.Thread.Start%2A> metody, jak pokazano w poniższym kodzie.  
  
```vb  
newThread.Start()  
```  
  
 Aby zatrzymać wykonanie wątku, użyj <xref:System.Threading.Thread.Abort%2A> metody, jak pokazano w poniższym kodzie.  
  
```vb  
newThread.Abort()  
```  
  
 Oprócz uruchamianie i zatrzymywanie wątków, można również wstrzymać wątków przez wywołanie metody <xref:System.Threading.Thread.Sleep%2A> lub <xref:System.Threading.Thread.Suspend%2A> metody wznowić wątku zawieszonym przy użyciu <xref:System.Threading.Thread.Resume%2A> metody i zniszcz wątku przy użyciu <xref:System.Threading.Thread.Abort%2A> — metoda  
  
### <a name="thread-methods"></a>Metody wątku  
 W poniższej tabeli przedstawiono niektóre metody, których można użyć do kontrolowania poszczególnych wątków.  
  
|Metoda|Akcja|  
|------------|------------|  
|<xref:System.Threading.Thread.Start%2A>|Powoduje, że wątku w celu rozpoczęcia.|  
|<xref:System.Threading.Thread.Sleep%2A>|Wstrzymuje wątku przez określony czas.|  
|<xref:System.Threading.Thread.Suspend%2A>|Wstrzymuje wątku po osiągnięciu bezpiecznym.|  
|<xref:System.Threading.Thread.Abort%2A>|Zatrzymuje wątek bezpiecznym.|  
|<xref:System.Threading.Thread.Resume%2A>|Ponowne uruchomienie wątku zawieszonym|  
|<xref:System.Threading.Thread.Join%2A>|Powoduje, że bieżący wątek oczekiwania na zakończenie innego wątku. Jeśli jest używany z wartości limitu czasu, ta metoda zwraca `True` Jeśli wątek zakończy działanie w przydzielonym czasie.|  
  
### <a name="safe-points"></a>Punkty bezpieczeństwa  
 Większość tych metod nie wymaga wyjaśnień, ale pojęcie *punkty bezpieczeństwa* mogą być nowe dla Ciebie. Punkty bezpieczeństwa, są lokalizacje w kodzie, gdzie jest bezpieczne dla środowiska CLR na wykonywanie automatycznego *wyrzucanie elementów bezużytecznych*, proces zwalniania zmienne i odzyskiwanie pamięci. Podczas wywoływania <xref:System.Threading.Thread.Abort%2A> lub <xref:System.Threading.Thread.Suspend%2A> metoda wątku, środowisko uruchomieniowe języka wspólnego analizuje kod i określa lokalizację odpowiednią lokalizację dla wątku przestanie działać.  
  
### <a name="thread-properties"></a>Właściwości wątku  
 Wątki również zawierać kilka właściwości przydatne, jak pokazano w poniższej tabeli:  
  
|Właściwość|Wartość|  
|--------------|-----------|  
|<xref:System.Threading.Thread.IsAlive%2A>|Zawiera wartość `True` czy wątku jest aktywna.|  
|<xref:System.Threading.Thread.IsBackground%2A>|Pobiera lub ustawia wartość Boolean wskazującą, czy wątek ma lub powinny być wątku w tle. Wątki w tle są podobne do wątki pierwszoplanowe, ale wątku w tle nie zapobiega proces zatrzymywania. Po zatrzymaniu wszystkie wątki pierwszego planu, które należą do procesów, środowisko uruchomieniowe języka wspólnego kończy proces po wywołaniu <xref:System.Threading.Thread.Abort%2A> metoda wątki w tle, które są nadal aktywne.|  
|<xref:System.Threading.Thread.Name%2A>|Pobiera lub ustawia nazwę wątku. Najczęściej używane do odnajdywania poszczególnych wątków podczas debugowania.|  
|<xref:System.Threading.Thread.Priority%2A>|Pobiera lub ustawia wartość, która jest używana przez system operacyjny priorytety planowania wątków.|  
|<xref:System.Threading.Thread.ThreadState%2A>|Zawiera wartość, która opisuje stanu lub stany wątku.|  
  
## <a name="thread-priorities"></a>Priorytety wątku  
 Każdy wątek ma właściwość priorytet, która określa, jak duże lub małe wycinka czasu procesora, które ma wykonać. System operacyjny przydziela dłużej przedziały czasu, aby wątki o wysokim priorytecie i krótszy przedziały czasu, aby wątki o niskim priorytecie. Nowe wątki są tworzone z wartością `Normal`, można jednak zmienić <xref:System.Threading.Thread.Priority%2A> wszelkie wartości dla właściwości <xref:System.Threading.ThreadPriority> wyliczenia.  
  
 Zobacz <xref:System.Threading.ThreadPriority> szczegółowy opis różnych priorytetów wątku.  
  
## <a name="foreground-and-background-threads"></a>Wątki pierwszego planu i tła  
 A *wątku na pierwszym planie* działa przez czas nieokreślony, podczas gdy *wątku w tle* zatrzymuje się, jak ostatni wątek pierwszego planu została zatrzymana. Można użyć <xref:System.Threading.Thread.IsBackground%2A> właściwości do określania, lub zmienić stan wątku w tle.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Threading.Thread>  
 [Synchronizacja wątku (Visual Basic)](../../../../visual-basic/programming-guide/concepts/threading/thread-synchronization.md)  
 [Parametry i wartości zwracane dla procedur wielowątkowości (Visual Basic)](../../../../visual-basic/programming-guide/concepts/threading/parameters-and-return-values-for-multithreaded-procedures.md)  
 [Wątkowość (Visual Basic)](../../../../visual-basic/programming-guide/concepts/threading/index.md)
