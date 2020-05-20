---
title: Serializowanie przepływów pracy i działań do i z plików XAML
description: Ten artykuł zawiera omówienie serializowania definicji przepływu pracy i pracy z definicjami przepływu pracy XAML w programie Workflow Foundation.
ms.date: 03/30/2017
ms.assetid: 37685b32-24e3-4d72-88d8-45d5fcc49ec2
ms.openlocfilehash: 168dbc9a36cfa80c15fddc7481e986d1ce383adb
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2020
ms.locfileid: "83421348"
---
# <a name="serialize-workflows-and-activities-to-and-from-xaml"></a>Serializowanie przepływów pracy i działań do i z języka XAML

Oprócz kompilowania do typów, które są zawarte w zestawach, definicje przepływu pracy mogą być również serializowane do języka XAML. Te serializowane definicje można ponownie załadować do edycji lub inspekcji, przekazywać do systemu kompilacji dla kompilacji lub ładowane i wywoływane. Ten temat zawiera omówienie serializowania definicji przepływu pracy i pracy z definicjami przepływu pracy XAML.

## <a name="work-with-xaml-workflow-definitions"></a>Korzystanie z definicji przepływu pracy XAML

Aby utworzyć definicję przepływu pracy dla serializacji, <xref:System.Activities.ActivityBuilder> używana jest Klasa. Tworzenie programu <xref:System.Activities.ActivityBuilder> jest bardzo podobne do tworzenia <xref:System.Activities.DynamicActivity> . Wszystkie żądane argumenty są określone i są konfigurowane działania, które stanowią zachowanie. W poniższym przykładzie `Add` jest tworzone działanie, które przyjmuje dwa argumenty wejściowe, dodaje je razem i zwraca wynik. Ponieważ to działanie zwraca wynik, <xref:System.Activities.ActivityBuilder%601> używana jest Klasa generyczna.

[!code-csharp[CFX_WorkflowApplicationExample#41](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#41)]

Każde <xref:System.Activities.DynamicActivityProperty> wystąpienie reprezentuje jeden z argumentów wejściowych dla przepływu pracy, a <xref:System.Activities.ActivityBuilder.Implementation%2A> zawiera działania, które tworzą logikę przepływu pracy. Należy zauważyć, że wyrażenia r-Value w tym przykładzie są Visual Basic Expressions. Wyrażenia lambda nie można serializować do języka XAML, chyba że <xref:System.Activities.Expressions.ExpressionServices.Convert%2A> jest używany. Jeśli serializowane przepływy pracy mają być otwierane lub edytowane w Projektancie przepływu pracy, należy użyć wyrażeń Visual Basic. Aby uzyskać więcej informacji, zobacz [Tworzenie przepływów pracy, działań i wyrażeń przy użyciu kodu](authoring-workflows-activities-and-expressions-using-imperative-code.md)bezwzględnego.

Aby serializować definicję przepływu pracy reprezentowanego przez <xref:System.Activities.ActivityBuilder> wystąpienie do języka XAML, użyj polecenia <xref:System.Activities.XamlIntegration.ActivityXamlServices> do utworzenia <xref:System.Xaml.XamlWriter> , a następnie użyj polecenia, <xref:System.Xaml.XamlServices> Aby serializować definicję przepływu pracy przy użyciu <xref:System.Xaml.XamlWriter> . <xref:System.Activities.XamlIntegration.ActivityXamlServices>ma metody mapowania <xref:System.Activities.ActivityBuilder> wystąpień do i z XAML oraz ładowania przepływów pracy XAML i zwracania <xref:System.Activities.DynamicActivity> , które mogą być wywoływane. W poniższym przykładzie <xref:System.Activities.ActivityBuilder> wystąpienie z poprzedniego przykładu jest serializowane do ciągu i zapisywane w pliku.

```csharp
// Serialize the workflow to XAML and store it in a string.
StringBuilder sb = new StringBuilder();
StringWriter tw = new StringWriter(sb);
XamlWriter xw = ActivityXamlServices.CreateBuilderWriter(new XamlXmlWriter(tw, new XamlSchemaContext()));
XamlServices.Save(xw, ab);
string serializedAB = sb.ToString();

// Display the XAML to the console.
Console.WriteLine(serializedAB);

// Serialize the workflow to XAML and save it to a file.
StreamWriter sw = File.CreateText(@"C:\Workflows\add.xaml");
XamlWriter xw2 = ActivityXamlServices.CreateBuilderWriter(new XamlXmlWriter(sw, new XamlSchemaContext()));
XamlServices.Save(xw2, ab);
sw.Close();
```

Poniższy przykład reprezentuje serializowany przepływ pracy.

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

Aby załadować serializowany przepływ pracy, użyj <xref:System.Activities.XamlIntegration.ActivityXamlServices> <xref:System.Activities.XamlIntegration.ActivityXamlServices.Load%2A> metody. Spowoduje to przedefiniowanie serializowanej definicji przepływu pracy i zwrócenie <xref:System.Activities.DynamicActivity> , która reprezentuje definicję przepływu pracy. Należy pamiętać, że kod XAML nie jest deserializowany do momentu <xref:System.Activities.Activity.CacheMetadata%2A> wywołania w treści <xref:System.Activities.DynamicActivity> procesu walidacji. Jeśli walidacja nie jest jawnie wywoływana, jest wykonywana po wywołaniu przepływu pracy. Jeśli definicja przepływu pracy XAML jest nieprawidłowa, <xref:System.ArgumentException> zostanie zgłoszony wyjątek. Wszystkie wyjątki zgłoszone przez funkcję <xref:System.Activities.Activity.CacheMetadata%2A> ucieczki z wywołania do <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A> i muszą być obsługiwane przez wywołującego. W poniższym przykładzie serializowany przepływ pracy z poprzedniego przykładu jest ładowany i wywoływany przy użyciu <xref:System.Activities.WorkflowInvoker> .

[!code-csharp[CFX_WorkflowApplicationExample#43](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#43)]

Po wywołaniu tego przepływu pracy następujące dane wyjściowe są wyświetlane w konsoli programu.

**25 + 15**\
**40**

> [!NOTE]
> Aby uzyskać więcej informacji na temat wywoływania przepływów pracy za pomocą argumentów wejściowych i wyjściowych, zobacz [using WorkflowInvoker and WorkflowApplication](using-workflowinvoker-and-workflowapplication.md) i <xref:System.Activities.WorkflowInvoker.Invoke%2A> .

Jeśli serializowany przepływ pracy zawiera wyrażenia języka C#, <xref:System.Activities.XamlIntegration.ActivityXamlServicesSettings> wystąpienie z <xref:System.Activities.XamlIntegration.ActivityXamlServicesSettings.CompileExpressions%2A> ustawioną jego właściwością `true` musi być przesyłane jako parametr do <xref:System.Activities.XamlIntegration.ActivityXamlServices.Load%2A?displayProperty=nameWithType> , w przeciwnym razie <xref:System.NotSupportedException> zostanie wygenerowany komunikat podobny do następującego: **Typ działania wyrażenia "CSharpValue" 1 "wymaga kompilacji, aby można było ją uruchomić.  Upewnij się, że przepływ pracy został skompilowany.**

```csharp
ActivityXamlServicesSettings settings = new ActivityXamlServicesSettings
{
    CompileExpressions = true
};

DynamicActivity<int> wf = ActivityXamlServices.Load(new StringReader(serializedAB), settings) as DynamicActivity<int>;
```

Aby uzyskać więcej informacji, zobacz [wyrażenia języka C#](csharp-expressions.md).

Można także załadować seryjną definicję przepływu pracy do <xref:System.Activities.ActivityBuilder> wystąpienia przy użyciu <xref:System.Activities.XamlIntegration.ActivityXamlServices> <xref:System.Activities.XamlIntegration.ActivityXamlServices.CreateBuilderReader%2A> metody. Po załadowaniu serializowanego przepływu pracy do <xref:System.Activities.ActivityBuilder> wystąpienia można go sprawdzić i zmodyfikować. Jest to przydatne w przypadku autorów projektanta niestandardowego przepływu pracy i oferuje mechanizm zapisywania i ponownego ładowania definicji przepływu pracy podczas procesu projektowania. W poniższym przykładzie załadowano seryjną definicję przepływu pracy z poprzedniego przykładu, a jej właściwości są kontrolowane.

[!code-csharp[CFX_WorkflowApplicationExample#44](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#44)]
