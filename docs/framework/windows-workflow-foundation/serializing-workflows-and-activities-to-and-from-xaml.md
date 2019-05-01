---
title: Serializowanie przepływów pracy i działań do i z plików XAML
ms.date: 03/30/2017
ms.assetid: 37685b32-24e3-4d72-88d8-45d5fcc49ec2
ms.openlocfilehash: 70ee2e8e0c457e9db2853935ef95b86c7f903fc3
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62004643"
---
# <a name="serializing-workflows-and-activities-to-and-from-xaml"></a>Serializowanie przepływów pracy i działań do i z plików XAML
Oprócz jest kompilowane na typy, które są zawarte w zestawach, definicji przepływu pracy może być serializowany do XAML. Te definicje serializacji, które można wykorzystać do edycji lub inspekcji, przekazywane do systemu kompilacji w celu kompilacji, lub załadowane i wywołana. Ten temat zawiera omówienie serializacji definicji przepływu pracy i Praca z XAML definicji przepływu pracy.  
  
## <a name="working-with-xaml-workflow-definitions"></a>Praca z definicji przepływu pracy XAML  
 Aby utworzyć definicję przepływu pracy do serializacji, <xref:System.Activities.ActivityBuilder> klasa jest używana. Tworzenie <xref:System.Activities.ActivityBuilder> jest bardzo podobny do procesu tworzenia <xref:System.Activities.DynamicActivity>. Żądany argumenty są określone, a wchodzących w skład zachowanie działania są skonfigurowane. W poniższym przykładzie `Add` utworzeniu działania, który przyjmuje dwa argumenty wejściowe, dodaje je ze sobą i zwraca wynik. Ponieważ to działanie zwraca wynik ogólny <xref:System.Activities.ActivityBuilder%601> klasa jest używana.  
  
 [!code-csharp[CFX_WorkflowApplicationExample#41](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#41)]  
  
 Każdy z <xref:System.Activities.DynamicActivityProperty> wystąpień stanowi jeden z argumentów wejściowych w przepływie pracy i <xref:System.Activities.ActivityBuilder.Implementation%2A> zawiera działania, które tworzą logikę przepływu pracy. Należy zauważyć, że wyrażenia r-wartości, w tym przykładzie wyrażeń języka Visual Basic. Wyrażenia lambda nie są możliwe do serializacji do XAML chyba że <xref:System.Activities.Expressions.ExpressionServices.Convert%2A> jest używany. Jeśli Zserializowany przepływy pracy są przeznaczone do można otworzyć lub edytować w Projektancie przepływu pracy, a następnie używać wyrażeń języka Visual Basic. Aby uzyskać więcej informacji, zobacz [tworzenia przepływów pracy, działań i wyrażeń przy użyciu technologii kodu](authoring-workflows-activities-and-expressions-using-imperative-code.md).  
  
 Do serializacji definicji przepływu pracy, reprezentowane przez <xref:System.Activities.ActivityBuilder> wystąpienia XAML, użyj <xref:System.Activities.XamlIntegration.ActivityXamlServices> utworzyć <xref:System.Xaml.XamlWriter>, a następnie użyj <xref:System.Xaml.XamlServices> serializować definicji przepływu pracy przy użyciu <xref:System.Xaml.XamlWriter>. <xref:System.Activities.XamlIntegration.ActivityXamlServices> zawiera metody, aby zamapować <xref:System.Activities.ActivityBuilder> wystąpień do i z XAML i załadować przepływów pracy XAML i zwracają <xref:System.Activities.DynamicActivity> może być wywołana. W poniższym przykładzie <xref:System.Activities.ActivityBuilder> wystąpienia z poprzedniego przykładu serializowana na ciąg, a także zapisywane w pliku.  
  
```csharp  
// Serialize the workflow to XAML and store it in a string.  
StringBuilder sb = new StringBuilder();  
StringWriter tw = new StringWriter(sb);  
XamlWriter xw = ActivityXamlServices.CreateBuilderWriter(new XamlXmlWriter(tw, new XamlSchemaContext()));  
XamlServices.Save(xw , ab);  
string serializedAB = sb.ToString();  
  
// Display the XAML to the console.  
Console.WriteLine(serializedAB);  
  
// Serialize the workflow to XAML and save it to a file.  
StreamWriter sw = File.CreateText(@"C:\Workflows\add.xaml");  
XamlWriter xw2 = ActivityXamlServices.CreateBuilderWriter(new XamlXmlWriter(sw, new XamlSchemaContext()));  
XamlServices.Save(xw2, ab);  
sw.Close();  
```  
  
 Poniższy przykład przedstawia Zserializowany przepływu pracy.  
  
```xaml  
<Activity   
  x:TypeArguments="x:Int32"   
  x:Class="Add"   
  xmlns="http://schemas.microsoft.com/netfx/2009/xaml/activities"   
  xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml">  
  <x:Members>  
    <x:Property Name="Operand1" Type="InArgument(x:Int32)" />  
    <x:Property Name="Operand2" Type="InArgument(x:Int32)" />  
  </x:Members>  
  <Sequence>  
    <WriteLine Text="[Operand1.ToString() + " + " + Operand2.ToString()]" />  
    <Assign x:TypeArguments="x:Int32" Value="[Operand1 + Operand2]">  
      <Assign.To>  
        <OutArgument x:TypeArguments="x:Int32">  
          <ArgumentReference x:TypeArguments="x:Int32" ArgumentName="Result" />  
          </OutArgument>  
      </Assign.To>  
    </Assign>  
  </Sequence>  
</Activity>  
```  
  
 Ładowanie Zserializowany przepływu pracy, <xref:System.Activities.XamlIntegration.ActivityXamlServices> <xref:System.Activities.XamlIntegration.ActivityXamlServices.Load%2A> metoda jest używana. To definicja przepływu pracy serializacji przyjmuje i zwraca <xref:System.Activities.DynamicActivity> reprezentujący definicji przepływu pracy. Należy zauważyć, że XAML nie wykonać deserializacji do momentu <xref:System.Activities.Activity.CacheMetadata%2A> jest wywoływana w treści <xref:System.Activities.DynamicActivity> w procesie weryfikacji. Jeśli weryfikacja nie została jawnie wywołana. następnie jest wykonywane po wywołaniu przepływu pracy. Jeśli definicja przepływu pracy XAML jest nieprawidłowy, a następnie <xref:System.ArgumentException> wyjątku. Wyjątki zgłaszane z <xref:System.Activities.Activity.CacheMetadata%2A> wyjścia z wywołania <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A> i muszą być obsługiwane przez obiekt wywołujący. W poniższym przykładzie jest ładowany i wywoływana przy użyciu serializowanej przepływu pracy z poprzedniego przykładu <xref:System.Activities.WorkflowInvoker>.  
  
 [!code-csharp[CFX_WorkflowApplicationExample#43](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#43)]  
  
 Po wywołaniu tego przepływu pracy następujące dane wyjściowe są wyświetlane w konsoli.  
  
 **25 + 15**  
**40**    
> [!NOTE]
>  Aby uzyskać więcej informacji na temat wywoływania przepływy pracy za pomocą argumentów wejściowych i wyjściowych, zobacz [przy użyciu obiektu WorkflowInvoker i WorkflowApplication](using-workflowinvoker-and-workflowapplication.md) i <xref:System.Activities.WorkflowInvoker.Invoke%2A>.  
  
 Jeśli Zserializowany przepływ pracy zawiera C# wyrażenia, a następnie <xref:System.Activities.XamlIntegration.ActivityXamlServicesSettings> wystąpienia z jego <xref:System.Activities.XamlIntegration.ActivityXamlServicesSettings.CompileExpressions%2A> właściwością `true` muszą być przekazywane jako parametr do <xref:System.Activities.XamlIntegration.ActivityXamlServices.Load%2A?displayProperty=nameWithType>, w przeciwnym razie <xref:System.NotSupportedException> zostanie zwrócony komunikat podobny do następującego: `Expression Activity type 'CSharpValue`1' wymaga kompilacji, aby można było uruchomić.  Upewnij się, że przepływ pracy został skompilowany. "  
  
```csharp  
ActivityXamlServicesSettings settings = new ActivityXamlServicesSettings  
{  
    CompileExpressions = true  
};  
  
DynamicActivity<int> wf = ActivityXamlServices.Load(new StringReader(serializedAB), settings) as DynamicActivity<int>;  
```  
  
 Aby uzyskać więcej informacji, zobacz [ C# wyrażeń](csharp-expressions.md).  
  
 Definicja przepływu pracy serializacji, również mogą być ładowane do <xref:System.Activities.ActivityBuilder> wystąpienia przy użyciu <xref:System.Activities.XamlIntegration.ActivityXamlServices> <xref:System.Activities.XamlIntegration.ActivityXamlServices.CreateBuilderReader%2A> metody. Po załadowaniu Zserializowany przepływu pracy do <xref:System.Activities.ActivityBuilder> wystąpienia można sprawdzić i modyfikować. Jest to użyteczne dla autorów projektanta niestandardowych przepływów pracy i udostępnia mechanizm do zapisywania i ponownego ładowania definicji przepływu pracy podczas procesu projektowania. W poniższym przykładzie jest ładowany definicji przepływu pracy serializacji z poprzedniego przykładu i jego właściwości są kontrolowane.  
  
 [!code-csharp[CFX_WorkflowApplicationExample#44](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#44)]
