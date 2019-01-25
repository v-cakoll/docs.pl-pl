---
title: Tworzenie działań asynchronicznych w WF
ms.date: 03/30/2017
ms.assetid: 497e81ed-5eef-460c-ba55-fae73c05824f
ms.openlocfilehash: 1b7fe1c5c998660f054d2ca060c108c758e36db7
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54650931"
---
# <a name="creating-asynchronous-activities-in-wf"></a>Tworzenie działań asynchronicznych w WF
<xref:System.Activities.AsyncCodeActivity> zawiera działanie autorzy klasę bazową do użycia, że umożliwia pochodne działania, aby zaimplementować logikę wykonanie asynchroniczne. Jest to przydatne dla działań niestandardowych, które należy wykonać pracę asynchroniczną bez przechowywania wątku harmonogramu przepływów pracy i zablokowanie wszelkich działań, które można uruchomić równolegle. Ten temat zawiera omówienie sposobu tworzenia niestandardowych działań asynchronicznych za pomocą <xref:System.Activities.AsyncCodeActivity>.  
  
## <a name="using-asynccodeactivity"></a>Za pomocą AsyncCodeActivity  
 <xref:System.Activities?displayProperty=nameWithType> zapewnia autorzy działań niestandardowych z różnych klas bazowych wymagania dotyczące tworzenia innego działania. Każdy z nich zawiera semantyczną określonego oraz autor przepływu pracy (i działanie środowiska uruchomieniowego) odpowiedniej umowy. <xref:System.Activities.AsyncCodeActivity> Działanie, które wykonuje pracę asynchronicznie względem harmonogramu jest oparte na działanie wątku i których wykonywania logiki jest wyrażona w kodzie zarządzanym. W wyniku pracę asynchroniczną, <xref:System.Activities.AsyncCodeActivity> może wywoływać punkt bezczynności podczas wykonywania. Ze względu na charakter volatile zadań asynchronicznych <xref:System.Activities.AsyncCodeActivity> zawsze tworzy bez blokady utrwalanie na czas trwania wykonywania działania. Zapobiega utrwalanie wystąpienia przepływu pracy w środku pracę asynchroniczną środowiska wykonawczego przepływów pracy i zapobiega także wystąpienia przepływu pracy z zwalnianie podczas wykonywania kodu asynchronicznego.  
  
### <a name="asynccodeactivity-methods"></a>Metody AsyncCodeActivity  
 Działania, które wynikają z <xref:System.Activities.AsyncCodeActivity> można utworzyć logikę wykonanie asynchroniczne przez zastąpienie <xref:System.Activities.AsyncCodeActivity.BeginExecute%2A> i <xref:System.Activities.AsyncCodeActivity.EndExecute%2A> metody z kodu niestandardowego. Gdy zostanie wywołana przez środowisko uruchomieniowe, te metody są przekazywane <xref:System.Activities.AsyncCodeActivityContext>. <xref:System.Activities.AsyncCodeActivityContext> umożliwia autorowi działania zapewnienie udostępnionego stanu między <xref:System.Activities.AsyncCodeActivity.BeginExecute%2A> /  <xref:System.Activities.AsyncCodeActivity.EndExecute%2A> w kontekście <xref:System.Activities.AsyncCodeActivityContext.UserState%2A> właściwości. W poniższym przykładzie `GenerateRandom` działania generuje losową liczbę asynchronicznie.  
  
 [!code-csharp[CFX_ActivityExample#8](../../../samples/snippets/csharp/VS_Snippets_CFX/CFX_ActivityExample/cs/Program.cs#8)]  
  
 Poprzednie działanie przykład pochodzi z <xref:System.Activities.AsyncCodeActivity%601>, i ma z podwyższonym poziomem uprawnień `OutArgument<int>` o nazwie `Result`. Wartość zwrócona przez obiekt `GetRandom` metody jest wyodrębniany i zwrócony przez <xref:System.Activities.AsyncCodeActivity%601.EndExecute%2A> przesłonięć i ta wartość jest ustawiana jako `Result` wartość. Asynchroniczne działania, które nie zwracają wynik powinien pochodzić od <xref:System.Activities.AsyncCodeActivity>. W poniższym przykładzie `DisplayRandom` działania jest zdefiniowany, który pochodzi od klasy <xref:System.Activities.AsyncCodeActivity>. To działanie jest podobne `GetRandom` działania, ale zamiast zwracać wynik zostanie wyświetlony komunikat do konsoli.  
  
 [!code-csharp[CFX_ActivityExample#11](../../../samples/snippets/csharp/VS_Snippets_CFX/CFX_ActivityExample/cs/Program.cs#11)]  
  
 Należy pamiętać, że ponieważ nie zwraca żadnej wartości `DisplayRandom` używa <xref:System.Action> zamiast <xref:System.Func%602> do wywołania, jego delegata i delegata nie zwraca żadnej wartości.  
  
 <xref:System.Activities.AsyncCodeActivity> udostępnia również <xref:System.Activities.AsyncCodeActivity.Cancel%2A> zastąpienia. Gdy <xref:System.Activities.AsyncCodeActivity.BeginExecute%2A> i <xref:System.Activities.AsyncCodeActivity.EndExecute%2A> są odpowiednich zastąpień <xref:System.Activities.AsyncCodeActivity.Cancel%2A> jest opcjonalna i może zostać zastąpiona, więc działanie można wyczyścić stanu zaległe asynchroniczne podczas jego anulowana lub przerwana. Jeśli oczyszczania jest możliwe i `AsyncCodeActivity.ExecutingActivityInstance.IsCancellationRequested` jest `true`, działania powinny wywoływać <xref:System.Activities.AsyncCodeActivityContext.MarkCanceled%2A>. Wyjątki zgłaszane przez tę metodę jest krytyczny dla wystąpienia przepływu pracy.  
  
 [!code-csharp[CFX_ActivityExample#10](../../../samples/snippets/csharp/VS_Snippets_CFX/CFX_ActivityExample/cs/Program.cs#10)]  
  
### <a name="invoking-asynchronous-methods-on-a-class"></a>Wywoływanie metod asynchronicznych klasy  
 Wiele klas w [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] udostępniają funkcje asynchroniczne, a ta funkcja może być wywołana asynchronicznie za pomocą <xref:System.Activities.AsyncCodeActivity> na podstawie działania. W poniższym przykładzie tworzone jest działanie, które asynchronicznie tworzy plik przy użyciu <xref:System.IO.FileStream> klasy.  
  
 [!code-csharp[CFX_ActivityExample#12](../../../samples/snippets/csharp/VS_Snippets_CFX/CFX_ActivityExample/cs/Program.cs#12)]  
  
### <a name="sharing-state-between-the-beginexecute-and-endexecute-methods"></a>Udostępnianie stanu między BeginExecute i metodami EndExecute  
 W poprzednim przykładzie <xref:System.IO.FileStream> obiektu, który został utworzony w <xref:System.Activities.AsyncCodeActivity.BeginExecute%2A> uzyskano w <xref:System.Activities.AsyncCodeActivity.EndExecute%2A>. Jest to możliwe, ponieważ `file` zmienna została przekazana <xref:System.Activities.AsyncCodeActivityContext.UserState%2A?displayProperty=nameWithType> właściwość <xref:System.Activities.AsyncCodeActivity.BeginExecute%2A>. Jest to prawidłowe metody udostępniania stanu między <xref:System.Activities.AsyncCodeActivity.BeginExecute%2A> i <xref:System.Activities.AsyncCodeActivity.EndExecute%2A>. Będzie ona nieprawidłowa, aby użyć zmiennej składowej klasy pochodnej (`FileWriter` w tym przypadku) do udostępniania stanu między <xref:System.Activities.AsyncCodeActivity.BeginExecute%2A> i <xref:System.Activities.AsyncCodeActivity.EndExecute%2A> ponieważ obiektu działania mogą być przywoływane przez wiele wystąpień działania. Podjęto próbę użycia zmienną członkowską na udostępnianie stanu może spowodować wartości z jednej <xref:System.Activities.ActivityInstance> zastąpienia lub korzystanie z wartości z innej <xref:System.Activities.ActivityInstance>.  
  
### <a name="accessing-argument-values"></a>Uzyskiwanie dostępu do wartości argumentów  
 Środowisko <xref:System.Activities.AsyncCodeActivity> składa się z argumentów zdefiniowanych w ramach działania. Te argumenty są dostępne z <xref:System.Activities.AsyncCodeActivity.BeginExecute%2A> / <xref:System.Activities.AsyncCodeActivity.EndExecute%2A> zastępuje przy użyciu <xref:System.Activities.AsyncCodeActivityContext> parametru. Argumenty nie są dostępne w obiektu delegowanego, ale wartości argumentu lub żądane dane mogą być przekazane do delegata, o których za pomocą jej parametrów. W poniższym przykładzie losowy działanie generowania numer jest zdefiniowany, uzyskujący włącznie górną granicę z jego `Max` argumentu. Wartość argumentu jest przekazywany w do kodu asynchronicznego, gdy obiekt delegowany jest wywoływany.  
  
 [!code-csharp[CFX_ActivityExample#9](../../../samples/snippets/csharp/VS_Snippets_CFX/CFX_ActivityExample/cs/Program.cs#9)]  
  
### <a name="scheduling-actions-or-child-activities-using-asynccodeactivity"></a>Planowanie akcji lub działania podrzędne przy użyciu AsyncCodeActivity  
 <xref:System.Activities.AsyncCodeActivity> pochodne działań niestandardowych udostępnia metody wykonywania pracy asynchronicznie w odniesieniu do wątku przepływu pracy, ale nie zapewniają możliwość zaplanowania działania podrzędne lub akcji. Jednak zachowanie asynchroniczne można włączyć za pomocą Planowanie ponownego szkolenia działania podrzędne dzięki kompozycji. Asynchroniczne działania można utworzyć, a następnie składającą się z <xref:System.Activities.Activity> lub <xref:System.Activities.NativeActivity> pochodne działania, aby zapewnić zachowanie asynchroniczne i Planowanie ponownego szkolenia działania podrzędne lub akcji. Na przykład można utworzyć działania pochodzącą z <xref:System.Activities.Activity>, a jako jego implementacja <xref:System.Activities.Statements.Sequence> zawierający asynchroniczne działania również innych działań, które implementują logikę działania. Aby uzyskać więcej przykładów tworzenie działań przy użyciu <xref:System.Activities.Activity> i <xref:System.Activities.NativeActivity>, zobacz [jak: Utwórz działanie](../../../docs/framework/windows-workflow-foundation/how-to-create-an-activity.md) i [działania opcje autorstwa](../../../docs/framework/windows-workflow-foundation/activity-authoring-options-in-wf.md).  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Action>
- <xref:System.Func%602>
