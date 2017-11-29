---
title: "Tworzenie asynchroniczne działania WF"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 497e81ed-5eef-460c-ba55-fae73c05824f
caps.latest.revision: "9"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: f2fd247348050b8335f4f6354c88664d497dbbf2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="creating-asynchronous-activities-in-wf"></a>Tworzenie asynchroniczne działania WF
<xref:System.Activities.AsyncCodeActivity>udostępnia klasę podstawową do użycia, że umożliwia pochodnych działań do wykonania operacji asynchronicznych logiki autorów działania. Jest to przydatne dla działań niestandardowych, które należy wykonać zadanie asynchroniczne bez zawierający wątku harmonogramu przepływu pracy i blokuje żadnych działań, które można uruchomić równolegle. Ten temat zawiera omówienie sposobu tworzenia działań niestandardowych asynchronicznych za pomocą <xref:System.Activities.AsyncCodeActivity>.  
  
## <a name="using-asynccodeactivity"></a>Przy użyciu AsyncCodeActivity  
 <xref:System.Activities?displayProperty=nameWithType>zapewnia autorów działań niestandardowych z różnych klas podstawowych wymagania dotyczące tworzenia różnych działań. Każda z nich niesie semantycznego określonego i zapewnia Autor przepływu pracy (i środowiska uruchomieniowego działania) odpowiedniego kontraktu. <xref:System.Activities.AsyncCodeActivity> Działanie, które wykonuje pracę asynchronicznie względem harmonogramu jest oparte na działanie wątku i którego logiki wykonywania jest wyrażoną w kodzie zarządzanym. Wyniku przechodzi do asynchronicznego, <xref:System.Activities.AsyncCodeActivity> może wywoływać punkt bezczynne podczas wykonywania. Ze względu na specyfikę volatile asynchroniczne pracy <xref:System.Activities.AsyncCodeActivity> zawsze tworzy bloku nietrwałości dla wykonywania działania. Zapobiega utrwalanie wystąpienia przepływu pracy w środku asynchroniczne pracy środowiska uruchomieniowego przepływu pracy i uniemożliwia także programowi wystąpienia przepływu pracy z podczas zwalniania wykonuje asynchroniczne kodu.  
  
### <a name="asynccodeactivity-methods"></a>Metody AsyncCodeActivity  
 Działania, które pochodzą z <xref:System.Activities.AsyncCodeActivity> można utworzyć logiki wykonywania asynchronicznych przez zastąpienie <xref:System.Activities.AsyncCodeActivity.BeginExecute%2A> i <xref:System.Activities.AsyncCodeActivity.EndExecute%2A> metody o niestandardowych kodów. Po wywołaniu przez środowisko uruchomieniowe, te metody są przekazywane <xref:System.Activities.AsyncCodeActivityContext>. <xref:System.Activities.AsyncCodeActivityContext>umożliwia autorowi działania zapewniające udostępniania stanu między <xref:System.Activities.AsyncCodeActivity.BeginExecute%2A> /  <xref:System.Activities.AsyncCodeActivity.EndExecute%2A> w tym kontekście <xref:System.Activities.AsyncCodeActivityContext.UserState%2A> właściwości. W poniższym przykładzie `GenerateRandom` działania generuje losową liczbę asynchronicznie.  
  
 [!code-csharp[CFX_ActivityExample#8](../../../samples/snippets/csharp/VS_Snippets_CFX/CFX_ActivityExample/cs/Program.cs#8)]  
  
 Poprzednie działanie przykładzie pochodzi z <xref:System.Activities.AsyncCodeActivity%601>, i ma podwyższonym `OutArgument<int>` o nazwie `Result`. Wartość zwrócona przez `GetRandom` metoda jest wyodrębniany i zwrócony przez <xref:System.Activities.AsyncCodeActivity%601.EndExecute%2A> zastąpienie, a ta wartość jest ustawiana jako `Result` wartość. Asynchroniczne działań, które nie zwracają wynik powinien pochodzić od <xref:System.Activities.AsyncCodeActivity>. W poniższym przykładzie `DisplayRandom` działania zdefiniowano pochodzący od <xref:System.Activities.AsyncCodeActivity>. To działanie przypomina `GetRandom` działania, ale zamiast zwracać wynik zostanie wyświetlony komunikat do konsoli.  
  
 [!code-csharp[CFX_ActivityExample#11](../../../samples/snippets/csharp/VS_Snippets_CFX/CFX_ActivityExample/cs/Program.cs#11)]  
  
 Należy pamiętać, że ponieważ brak wartości zwracanej nie `DisplayRandom` używa <xref:System.Action> zamiast <xref:System.Func%602> można wywołać jej delegata i delegat nie zwraca żadnej wartości.  
  
 <xref:System.Activities.AsyncCodeActivity>dostępne są także <xref:System.Activities.AsyncCodeActivity.Cancel%2A> zastąpienia. Gdy <xref:System.Activities.AsyncCodeActivity.BeginExecute%2A> i <xref:System.Activities.AsyncCodeActivity.EndExecute%2A> są wymagane zastąpienia <xref:System.Activities.AsyncCodeActivity.Cancel%2A> jest opcjonalny i może zostać zastąpiona tak działania można wyczyścić stanu oczekujących asynchronicznych, gdy jest on anulowana lub przerwana. Jeśli oczyszczania jest możliwe i `AsyncCodeActivity.ExecutingActivityInstance.IsCancellationRequested` jest `true`, powinny wywoływać działania <xref:System.Activities.AsyncCodeActivityContext.MarkCanceled%2A>. Wszelkie wyjątki zgłaszane przez tę metodę jest krytyczny do wystąpienia przepływu pracy.  
  
 [!code-csharp[CFX_ActivityExample#10](../../../samples/snippets/csharp/VS_Snippets_CFX/CFX_ActivityExample/cs/Program.cs#10)]  
  
### <a name="invoking-asynchronous-methods-on-a-class"></a>Wywoływanie metod asynchronicznych klasy  
 Wiele klas w [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] umożliwić korzystanie z funkcji asynchronicznych, a ta funkcja może być wywoływany asynchronicznie za pomocą <xref:System.Activities.AsyncCodeActivity> na podstawie działania. W poniższym przykładzie z [przy użyciu AsyncOperationContext w działaniu](../../../docs/framework/windows-workflow-foundation/samples/using-asyncoperationcontext-in-an-activity-sample.md), utworzeniu działania, które asynchronicznie tworzy plik przy użyciu <xref:System.IO.FileStream> klasy.  
  
 [!code-csharp[CFX_ActivityExample#12](../../../samples/snippets/csharp/VS_Snippets_CFX/CFX_ActivityExample/cs/Program.cs#12)]  
  
### <a name="sharing-state-between-the-beginexecute-and-endexecute-methods"></a>Udostępniania stanu między BeginExecute i EndExecute metody  
 W poprzednim przykładzie <xref:System.IO.FileStream> obiektu, który został utworzony w <xref:System.Activities.AsyncCodeActivity.BeginExecute%2A> uzyskano w <xref:System.Activities.AsyncCodeActivity.EndExecute%2A>. Jest to możliwe, ponieważ `file` zmienna została przekazana <xref:System.Activities.AsyncCodeActivityContext.UserState%2A?displayProperty=nameWithType> właściwości w <xref:System.Activities.AsyncCodeActivity.BeginExecute%2A>. Jest to prawidłowa metoda udostępniania stanu między <xref:System.Activities.AsyncCodeActivity.BeginExecute%2A> i <xref:System.Activities.AsyncCodeActivity.EndExecute%2A>. Jest nieprawidłowe do używania zmiennej członkowskiej w klasie pochodnej (`FileWriter` w takim przypadku) do udostępniania stanu między <xref:System.Activities.AsyncCodeActivity.BeginExecute%2A> i <xref:System.Activities.AsyncCodeActivity.EndExecute%2A> ponieważ obiektu działania może odwoływać się wiele wystąpień działania. Podjęto próbę użycia zmienną członkowską do udostępniania stanu może spowodować wartości z jednego <xref:System.Activities.ActivityInstance> zastąpienia lub korzystanie z wartości z innej <xref:System.Activities.ActivityInstance>.  
  
### <a name="accessing-argument-values"></a>Uzyskiwanie dostępu do wartości argumentów  
 Środowisko <xref:System.Activities.AsyncCodeActivity> składa się z argumentami zdefiniowane w działaniu. Tych argumentów można uzyskać z <xref:System.Activities.AsyncCodeActivity.BeginExecute%2A> / <xref:System.Activities.AsyncCodeActivity.EndExecute%2A> zastępuje przy użyciu <xref:System.Activities.AsyncCodeActivityContext> parametru. Delegat, ale wartości argumentów nie można uzyskać dostępu do argumentów lub żądanych danych można przekazać do obiektu delegowanego przy użyciu jego parametrów. W poniższym przykładzie losowe działania generowania numer jest zdefiniowany uzyskujący włącznie górnej granicy z jego `Max` argumentu. Wartość argumentu jest przekazany do asynchronicznego kodu po wywołaniu obiektu delegowanego.  
  
 [!code-csharp[CFX_ActivityExample#9](../../../samples/snippets/csharp/VS_Snippets_CFX/CFX_ActivityExample/cs/Program.cs#9)]  
  
### <a name="scheduling-actions-or-child-activities-using-asynccodeactivity"></a>Planowanie akcje lub przy użyciu AsyncCodeActivity działania podrzędne  
 <xref:System.Activities.AsyncCodeActivity>pochodne działań niestandardowych udostępnia metody wykonywania pracy asynchronicznie w odniesieniu do wątku przepływu pracy, ale nie zapewniają możliwość planować działań podrzędnych lub akcji. Jednak asynchroniczne zachowanie można włączyć planowania działań podrzędnych za pomocą kompozycji. Asynchroniczne działania można utworzyć, a następnie składa się z <xref:System.Activities.Activity> lub <xref:System.Activities.NativeActivity> pochodzi z działania, aby zapewnić zachowanie asynchroniczne i planowania działań podrzędnych lub akcji. Na przykład można utworzyć działania pochodzącego od <xref:System.Activities.Activity>i jako jego implementacja <xref:System.Activities.Statements.Sequence> zawierające działanie asynchroniczne, jak również innych działań, które implementują logikę działania. Więcej przykładów dotyczących tworzenia działania przy użyciu <xref:System.Activities.Activity> i <xref:System.Activities.NativeActivity>, zobacz [porady: tworzenie działania](../../../docs/framework/windows-workflow-foundation/how-to-create-an-activity.md), [opcje tworzenia działania](../../../docs/framework/windows-workflow-foundation/activity-authoring-options-in-wf.md)i [złożone](../../../docs/framework/windows-workflow-foundation/samples/composite.md) przykłady działania.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Action>  
 <xref:System.Func%602>  
 [Przy użyciu AsyncOperationContext w działaniu](../../../docs/framework/windows-workflow-foundation/samples/using-asyncoperationcontext-in-an-activity-sample.md)
