---
ms.openlocfilehash: ab2907b05bff409fed9a370d5cbebbf3d1575d2f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "59981673"
---
### <a name="systemthreadingtaskstask-no-longer-throw-objectdisposedexception-after-object-is-disposed"></a>System.Threading.Tasks.Task nie zgłaszają już objectdisposedexception — po usunięciu obiektu

|   |   |
|---|---|
|Szczegóły|Z wyjątkiem <xref:System.Threading.Tasks.Task.System%23IAsyncResult%23AsyncWaitHandle>, <xref:System.Threading.Tasks.Task?displayProperty=name> metody nie zgłaszają już <xref:System.ObjectDisposedException?displayProperty=name> wyjątek po usunięciu obiektu. Ta zmiana umożliwia obsługę zadań buforowanych. Na przykład metoda może zwracać buforowane zadanie w celu reprezentowania już zakończonej operacji, zamiast przydzielać nowe zadanie. Było to niemożliwe w poprzednich wersjach programu .NET Framework, ponieważ każdy konsument zadania mógł je usunąć, co czyniło je bezużytecznym.|
|Sugestia|Należy pamiętać, że metody zadań mogą już nie generują <xref:System.ObjectDisposedException?displayProperty=name> w przypadkach, gdy obiekt zostanie usunięty. Jeśli aplikacja była w zależności od tego wyjątku, aby dowiedzieć się, że zadanie zostało usunięte, należy zaktualizować jawnie sprawdzić stan zadania przy użyciu <xref:System.Threading.Tasks.Task.Status>.|
|Zakres|Mały|
|Wersja|4.5|
|Typ|Środowisko uruchomieniowe|
