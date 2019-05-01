---
title: Właściwości a Argumenty
ms.date: 03/30/2017
ms.assetid: 14651389-4a49-4cbb-9ddf-c83fdc155df1
ms.openlocfilehash: a6ea4755599f18e8bbaa8187941623578d2168ac
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61962633"
---
# <a name="properties-vs-arguments"></a>Właściwości a Argumenty
Brak dostępnych kilka opcji przekazywania danych do działania. Oprócz używania <xref:System.Activities.InArgument>, działania mogą również być tworzone odbierające dane przy użyciu standardowych właściwości aparatu CLR lub publicznego <xref:System.Activities.ActivityAction> właściwości. W tym temacie omówiono sposób wybierania typu odpowiednią metodę.  
  
## <a name="using-clr-properties"></a>Za pomocą właściwości aparatu CLR  
 Przy przekazywaniu danych do działania, właściwości środowiska CLR (czyli metody publiczne, użyj elementów Get i Set procedury do udostępniania danych) są opcji, która ma najwięcej ograniczeń. Wartość parametru przekazywana do właściwości CLR musi być znane, podczas kompilowania rozwiązania; Ta wartość będzie taka sama dla każdego wystąpienia przepływu pracy. W ten sposób wartość przekazywana do właściwości CLR przypomina stałą zdefiniowana w kodzie; Ta wartość nie może zmienić okres aktywności i nie można zmienić dla różnych wystąpień działania. <xref:System.Activities.Expressions.InvokeMethod%601.MethodName%2A> Oto przykład CLR właściwości udostępnianych przez działanie; Nazwa metody, która wywołuje działania nie można zmienić w zależności od środowiska uruchomieniowego warunki i jest taka sama dla każdego wystąpienia działania.  
  
## <a name="using-arguments"></a>Za pomocą argumentów  
 Argumenty powinny być używane, gdy dane, jest oceniane tylko raz w okresie istnienia działanie; oznacza to, że jego wartość nie zmieni się w okresie istnienia działania, ale wartość mogą być różne dla różnych wystąpień działania. <xref:System.Activities.Statements.If.Condition%2A> Oto przykład obliczaniu raz, a wartość w związku z tym jest zdefiniowany jako argument. <xref:System.Activities.Statements.WriteLine.Text%2A> innym przykładem metodę, która powinna być zdefiniowana jako argument, ponieważ jest oceniane tylko raz podczas wykonywania działania, ale mogą być różne dla różnych wystąpień działania.  
  
## <a name="using-activityaction"></a>Za pomocą elementu ActivityAction.  
 Gdy danych powinna być oceniana wiele razy w okresie istnienia wykonania działania <xref:System.Activities.ActivityAction> powinny być używane. Na przykład <xref:System.Activities.Statements.While.Condition%2A> właściwości są obliczane dla każdej iteracji <xref:System.Activities.Statements.While> pętli. Jeśli <xref:System.Activities.InArgument> zostały użyte w tym celu, pętla nigdy nie wyjścia, ponieważ argument dla każdej iteracji może nie być ponownie oceniane i będzie zawsze zwróci ten sam wynik.
