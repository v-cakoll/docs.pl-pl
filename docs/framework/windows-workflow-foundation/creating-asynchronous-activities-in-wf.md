---
title: Tworzenie działań asynchronicznych w WF
description: Dowiedz się, jak tworzyć niestandardowe działania asynchroniczne przy użyciu metoda AsyncCodeActivity, które umożliwia pochodnym działaniom implementowanie logiki wykonywania asynchronicznego.
ms.date: 03/30/2017
ms.assetid: 497e81ed-5eef-460c-ba55-fae73c05824f
ms.openlocfilehash: f7ce0c0157791b34723feff185aed24bb56a4b3f
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2020
ms.locfileid: "83421530"
---
# <a name="creating-asynchronous-activities-in-wf"></a>Tworzenie działań asynchronicznych w WF
<xref:System.Activities.AsyncCodeActivity>zapewnia autorom działania klasę bazową, która umożliwia pochodnym działaniom implementowanie logiki asynchronicznego wykonywania. Jest to przydatne w przypadku działań niestandardowych, które muszą wykonywać działania asynchroniczne bez posiadania wątku harmonogramu przepływu pracy i blokowania wszystkich działań, które mogą być uruchamiane równolegle. Ten temat zawiera omówienie sposobu tworzenia niestandardowych działań asynchronicznych przy użyciu programu <xref:System.Activities.AsyncCodeActivity> .  
  
## <a name="using-asynccodeactivity"></a>Korzystanie z Metoda AsyncCodeActivity  
 <xref:System.Activities?displayProperty=nameWithType>zapewnia niestandardowe autorów działań z różnymi klasami podstawowymi dla różnych wymagań tworzenia działań. Każdy z nich ma określoną semantykę i udostępnia autora przepływu pracy (i środowiska uruchomieniowego działania) odpowiadającego mu kontraktu. <xref:System.Activities.AsyncCodeActivity>Działanie oparte na działaniu jest działaniem asynchronicznie względem wątku harmonogramu, którego logika wykonywania jest wyrażana w kodzie zarządzanym. W wyniku przetworzenia asynchronicznej, <xref:System.Activities.AsyncCodeActivity> może wywołać punkt bezczynności podczas wykonywania. Ze względu na nietrwałą naturę pracy asynchronicznej, <xref:System.Activities.AsyncCodeActivity> zawsze tworzy blok braku trwałości na czas wykonywania działania. Zapobiega to utrwalaniu wystąpienia przepływu pracy w trakcie pracy asynchronicznej w czasie wykonywania, a także zapobiega zwalnianiu wystąpienia przepływu pracy podczas wykonywania kodu asynchronicznego.  
  
### <a name="asynccodeactivity-methods"></a>Metody Metoda AsyncCodeActivity  
 Działania, które pochodzą z programu, <xref:System.Activities.AsyncCodeActivity> mogą tworzyć asynchroniczne wykonywanie logiki przez zastępowanie <xref:System.Activities.AsyncCodeActivity.BeginExecute%2A> <xref:System.Activities.AsyncCodeActivity.EndExecute%2A> metod i z kodem niestandardowym. Po wywołaniu przez środowisko uruchomieniowe te metody są przenoszone <xref:System.Activities.AsyncCodeActivityContext> . <xref:System.Activities.AsyncCodeActivityContext>umożliwia autorowi działania udostępnianie udostępnionego stanu we <xref:System.Activities.AsyncCodeActivity.BeginExecute%2A> /  <xref:System.Activities.AsyncCodeActivity.EndExecute%2A> <xref:System.Activities.AsyncCodeActivityContext.UserState%2A> właściwości kontekstu. W poniższym przykładzie `GenerateRandom` działanie generuje losową liczbę asynchronicznie.  
  
 [!code-csharp[CFX_ActivityExample#8](~/samples/snippets/csharp/VS_Snippets_CFX/CFX_ActivityExample/cs/Program.cs#8)]  
  
 Poprzednie przykładowe działanie pochodzi z <xref:System.Activities.AsyncCodeActivity%601> i ma podwyższony poziom `OutArgument<int>` o nazwie `Result` . Wartość zwracana przez `GetRandom` metodę jest wyodrębniana i zwracana przez <xref:System.Activities.AsyncCodeActivity%601.EndExecute%2A> przesłonięcie, a ta wartość jest ustawiana jako `Result` wartość. Działania asynchroniczne, które nie zwracają wyniku, powinny pochodzić od <xref:System.Activities.AsyncCodeActivity> . W poniższym przykładzie `DisplayRandom` zdefiniowano działanie, które pochodzi od <xref:System.Activities.AsyncCodeActivity> . To działanie jest podobne do `GetRandom` działania, ale zamiast zwracać wynik wyświetla komunikat w konsoli programu.  
  
 [!code-csharp[CFX_ActivityExample#11](~/samples/snippets/csharp/VS_Snippets_CFX/CFX_ActivityExample/cs/Program.cs#11)]  
  
 Zwróć uwagę, że ponieważ nie ma żadnej wartości zwracanej, program `DisplayRandom` używa elementu <xref:System.Action> instead of <xref:System.Func%602> do wywołania jego delegata, a delegat nie zwraca żadnej wartości.  
  
 <xref:System.Activities.AsyncCodeActivity>zapewnia również <xref:System.Activities.AsyncCodeActivity.Cancel%2A> przesłonięcie. Chociaż <xref:System.Activities.AsyncCodeActivity.BeginExecute%2A> i <xref:System.Activities.AsyncCodeActivity.EndExecute%2A> są wymagane przesłonięcia, <xref:System.Activities.AsyncCodeActivity.Cancel%2A> jest opcjonalne i można je zastąpić, aby działanie było oczyszczać stan asynchroniczny w momencie jego anulowania lub przerwania. Jeśli jest możliwe czyszczenie `AsyncCodeActivity.ExecutingActivityInstance.IsCancellationRequested` `true` , działanie powinno wywołać <xref:System.Activities.AsyncCodeActivityContext.MarkCanceled%2A> . Wszystkie wyjątki zgłoszone przez tę metodę są krytyczne dla wystąpienia przepływu pracy.  
  
 [!code-csharp[CFX_ActivityExample#10](~/samples/snippets/csharp/VS_Snippets_CFX/CFX_ActivityExample/cs/Program.cs#10)]  
  
### <a name="invoking-asynchronous-methods-on-a-class"></a>Wywoływanie metod asynchronicznych w klasie  
 Wiele klas w .NET Framework zapewnia funkcje asynchroniczne, a ta funkcja może być wywoływana asynchronicznie przy użyciu <xref:System.Activities.AsyncCodeActivity> działania opartego na bazie. W poniższym przykładzie jest tworzone działanie, które asynchronicznie tworzy plik za pomocą <xref:System.IO.FileStream> klasy.  
  
 [!code-csharp[CFX_ActivityExample#12](~/samples/snippets/csharp/VS_Snippets_CFX/CFX_ActivityExample/cs/Program.cs#12)]  
  
### <a name="sharing-state-between-the-beginexecute-and-endexecute-methods"></a>Stan udostępniania między metodami BeginExecute i EndExecute  
 W poprzednim przykładzie <xref:System.IO.FileStream> obiekt, który został utworzony w <xref:System.Activities.AsyncCodeActivity.BeginExecute%2A> , został uzyskany w <xref:System.Activities.AsyncCodeActivity.EndExecute%2A> . Jest to możliwe, ponieważ `file` zmienna została przeniesiona we <xref:System.Activities.AsyncCodeActivityContext.UserState%2A?displayProperty=nameWithType> właściwości w <xref:System.Activities.AsyncCodeActivity.BeginExecute%2A> . Jest to poprawna Metoda stanu udostępniania między <xref:System.Activities.AsyncCodeActivity.BeginExecute%2A> i <xref:System.Activities.AsyncCodeActivity.EndExecute%2A> . Użycie zmiennej składowej w klasie pochodnej ( `FileWriter` w tym przypadku) jest nieprawidłowe, aby można było udostępnić stan między <xref:System.Activities.AsyncCodeActivity.BeginExecute%2A> i <xref:System.Activities.AsyncCodeActivity.EndExecute%2A> ponieważ obiekt Activity może odwoływać się do wielu wystąpień działania. Próba użycia zmiennej składowej w celu udostępnienia stanu może spowodować powstanie wartości z jednego <xref:System.Activities.ActivityInstance> zastąpienia lub zużywania wartości z innego <xref:System.Activities.ActivityInstance> .  
  
### <a name="accessing-argument-values"></a>Uzyskiwanie dostępu do wartości argumentów  
 Środowisko <xref:System.Activities.AsyncCodeActivity> składa się z argumentów zdefiniowanych w działaniu. Do tych argumentów można uzyskać dostęp z <xref:System.Activities.AsyncCodeActivity.BeginExecute%2A> / <xref:System.Activities.AsyncCodeActivity.EndExecute%2A> przesłonięć przy użyciu <xref:System.Activities.AsyncCodeActivityContext> parametru. Nie można uzyskać dostępu do argumentów w delegatze, ale wartości argumentów lub inne żądane dane można przekazać do delegata przy użyciu jego parametrów. W poniższym przykładzie zdefiniowano losowe działanie generujące liczbę, które uzyskuje górną granicę z tego `Max` argumentu. Wartość argumentu jest przenoszona do kodu asynchronicznego, gdy obiekt delegowany jest wywoływany.  
  
 [!code-csharp[CFX_ActivityExample#9](~/samples/snippets/csharp/VS_Snippets_CFX/CFX_ActivityExample/cs/Program.cs#9)]  
  
### <a name="scheduling-actions-or-child-activities-using-asynccodeactivity"></a>Planowanie akcji lub działań podrzędnych przy użyciu metoda AsyncCodeActivity  
 <xref:System.Activities.AsyncCodeActivity>pochodne działania niestandardowe zapewniają metodę asynchronicznego wykonywania zadań w odniesieniu do wątku przepływu pracy, ale nie zapewniają możliwości planowania działań podrzędnych lub akcji. Jednak zachowanie asynchroniczne można włączyć w celu planowania działań podrzędnych za pomocą kompozycji. Działanie asynchroniczne można utworzyć, a następnie tworzyć z <xref:System.Activities.Activity> lub <xref:System.Activities.NativeActivity> pochodną aktywność, aby zapewnić asynchroniczne zachowanie i planowanie działań podrzędnych lub akcji. Na przykład można utworzyć działanie, które pochodzi od <xref:System.Activities.Activity> , i ma jako jego implementację, <xref:System.Activities.Statements.Sequence> zawierający działanie asynchroniczne, a także inne działania, które implementują logikę działania. Aby uzyskać więcej przykładów tworzenia działań za pomocą <xref:System.Activities.Activity> i <xref:System.Activities.NativeActivity> , zobacz [How to: Create a Activity](how-to-create-an-activity.md) and [Activity Authoring Options](activity-authoring-options-in-wf.md).  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Action>
- <xref:System.Func%602>
