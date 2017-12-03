---
title: "Serializacja przepływów pracy i działań do i z XAML"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 37685b32-24e3-4d72-88d8-45d5fcc49ec2
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 3be1c85a87896c176d5e81d2938418194d28b93b
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="serializing-workflows-and-activities-to-and-from-xaml"></a>Serializacja przepływów pracy i działań do i z XAML
Oprócz kompilowany do typów, które znajdują się w zestawach definicji przepływu pracy może być Zserializowany w języku XAML. Te definicje serializacji można wykorzystać do edycji lub inspekcję, przekazany do system kompilacji dla kompilacji, i załadować wywołany. Ten temat zawiera omówienie serializacji definicji przepływu pracy oraz pracy z definicji przepływu pracy XAML.  
  
## <a name="working-with-xaml-workflow-definitions"></a>Praca z definicji przepływu pracy XAML  
 Do tworzenia definicji przepływu pracy do serializacji, <xref:System.Activities.ActivityBuilder> klasa jest używana. Tworzenie <xref:System.Activities.ActivityBuilder> jest bardzo podobny do tworzenia <xref:System.Activities.DynamicActivity>. Podano argumenty żądanej i działania, które stanowią zachowanie są skonfigurowane. W poniższym przykładzie `Add` utworzeniu działania, który przyjmuje dwa argumenty wejściowe, dodaje je ze sobą i zwraca wynik. Ponieważ to działanie zwraca wynik, ogólnego <xref:System.Activities.ActivityBuilder%601> klasa jest używana.  
  
 [!code-csharp[CFX_WorkflowApplicationExample#41](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#41)]  
  
 Każdy z <xref:System.Activities.DynamicActivityProperty> wystąpień reprezentuje jeden z argumentów wejściowych w przepływie pracy oraz <xref:System.Activities.ActivityBuilder.Implementation%2A> zawiera działania, które tworzą logika przepływu pracy. Należy pamiętać, że wyrażenia r-wartości w tym przykładzie są wyrażeń języka Visual Basic. Wyrażenia lambda nie są do serializacji w języku XAML chyba że <xref:System.Activities.Expressions.ExpressionServices.Convert%2A> jest używany. Jeśli serializacji przepływy pracy mają można otworzyć lub edytować w Projektancie przepływów pracy, a następnie wyrażeń języka Visual Basic powinien być używany. [!INCLUDE[crdefault](../../../includes/crdefault-md.md)][Tworzenia przepływów pracy, działań i wyrażenia przy użyciu kodu Imperatywnych](../../../docs/framework/windows-workflow-foundation/authoring-workflows-activities-and-expressions-using-imperative-code.md).  
  
 Do serializacji definicji przepływu pracy reprezentowany przez <xref:System.Activities.ActivityBuilder> wystąpienia w języku XAML, użyj <xref:System.Activities.XamlIntegration.ActivityXamlServices> utworzyć <xref:System.Xaml.XamlWriter>, a następnie użyj <xref:System.Xaml.XamlServices> do serializacji definicji przepływu pracy przy użyciu <xref:System.Xaml.XamlWriter>. <xref:System.Activities.XamlIntegration.ActivityXamlServices>metody mapowania <xref:System.Activities.ActivityBuilder> wystąpień do i z XAML i załadować przepływów pracy XAML i zwracać <xref:System.Activities.DynamicActivity> może być wywołany. W poniższym przykładzie <xref:System.Activities.ActivityBuilder> wystąpienia z poprzedniego przykładu uszeregować w ciągu, a także zapisane w pliku.  
  
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
  
 Poniższy przykład przedstawia serializacji przepływu pracy.  
  
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
  
 Do załadowania serializacji przepływu pracy, <xref:System.Activities.XamlIntegration.ActivityXamlServices> <xref:System.Activities.XamlIntegration.ActivityXamlServices.Load%2A> metoda jest używana. To przyjmuje definicja Zserializowany przepływu pracy i zwraca <xref:System.Activities.DynamicActivity> reprezentujący definicji przepływu pracy. Należy pamiętać, że XAML nie jest zdeserializować do <xref:System.Activities.Activity.CacheMetadata%2A> jest wywoływana w treści <xref:System.Activities.DynamicActivity> w procesie weryfikacji. Jeśli weryfikacja nie została jawnie wywołana. jest on również wykonywane po wywołaniu przepływ pracy. Jeśli XAML definicji przepływu pracy jest nieprawidłowy, a następnie <xref:System.Argument> wyjątku. Wszelkie wyjątki zgłaszane z <xref:System.Activities.Activity.CacheMetadata%2A> ucieczki z wywołania <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A> i muszą być obsługiwane przez obiekt wywołujący. W poniższym przykładzie serializacji przepływu pracy z poprzedniego przykładu jest załadowany i wywoływane przy użyciu <xref:System.Activities.WorkflowInvoker>.  
  
 [!code-csharp[CFX_WorkflowApplicationExample#43](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#43)]  
  
 Po wywołaniu tego przepływu pracy następujące dane wyjściowe są wyświetlane w konsoli.  
  
 **25 + 15**  
**40**    
> [!NOTE]
>  [!INCLUDE[crabout](../../../includes/crabout-md.md)]wywoływanie przepływy pracy argumentów wejściowych i wyjściowych, zobacz [przy użyciu WorkflowInvoker i działanie obiektu WorkflowApplication](../../../docs/framework/windows-workflow-foundation/using-workflowinvoker-and-workflowapplication.md) i <xref:System.Activities.WorkflowInvoker.Invoke%2A>.  
  
 Jeśli serializacji przepływ pracy zawiera wyrażenia języka C#, a następnie <xref:System.Activities.XamlIntegration.ActivityXamlServicesSettings> wystąpienia z jego <xref:System.Activities.XamlIntegration.ActivityXamlServicesSettings.CompileExpressions%2A> ustawioną właściwość `true` muszą być przekazywane jako parametr <xref:System.Activities.XamlIntegration.ActivityXamlServices.Load%2A?displayProperty=nameWithType>, w przeciwnym razie <xref:System.NotSupportedException> zostanie zgłoszony z komunikatu podobnego do następujące: `Expression Activity type 'CSharpValue`1" wymaga kompilacji, aby można było uruchomić.  Upewnij się, że przepływ pracy został skompilowany. "  
  
```csharp  
ActivityXamlServicesSettings settings = new ActivityXamlServicesSettings  
{  
    CompileExpressions = true  
};  
  
DynamicActivity<int> wf = ActivityXamlServices.Load(new StringReader(serializedAB), settings) as DynamicActivity<int>;  
```  
  
 [!INCLUDE[crdefault](../../../includes/crdefault-md.md)][Wyrażeń C#](../../../docs/framework/windows-workflow-foundation/csharp-expressions.md).  
  
 Definicja Zserializowany przepływu pracy mogą także zostać załadowane do <xref:System.Activities.ActivityBuilder> wystąpienia przy użyciu <xref:System.Activities.XamlIntegration.ActivityXamlServices> <xref:System.Activities.XamlIntegration.ActivityXamlServices.CreateBuilderReader%2A> metody. Po załadowaniu serializacji przepływu pracy do <xref:System.Activities.ActivityBuilder> wystąpienia można sprawdzić i modyfikować. Jest to użyteczne dla autorów projektanta niestandardowego przepływu pracy i udostępnia mechanizm dla zapisywanie i ponowne załadowanie definicji przepływu pracy podczas tworzenia projektu. W poniższym przykładzie jest ładowany definicja Zserializowany przepływu pracy z poprzedniego przykładu, a jego właściwości są kontrolowane.  
  
 [!code-csharp[CFX_WorkflowApplicationExample#44](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#44)]
