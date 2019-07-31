---
title: Serializowanie przepływów pracy i działań do i z plików XAML
ms.date: 03/30/2017
ms.assetid: 37685b32-24e3-4d72-88d8-45d5fcc49ec2
ms.openlocfilehash: c18afa7232adabc4f1c4e17fde993064b9189e39
ms.sourcegitcommit: 3eeea78f52ca771087a6736c23f74600cc662658
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/31/2019
ms.locfileid: "68671894"
---
# <a name="serialize-workflows-and-activities-to-and-from-xaml"></a>Serializowanie przepływów pracy i działań do i z języka XAML

Oprócz kompilowania do typów, które są zawarte w zestawach, definicje przepływu pracy mogą być również serializowane do języka XAML. Te serializowane definicje można ponownie załadować do edycji lub inspekcji, przekazywać do systemu kompilacji dla kompilacji lub ładowane i wywoływane. Ten temat zawiera omówienie serializowania definicji przepływu pracy i pracy z definicjami przepływu pracy XAML.

## <a name="work-with-xaml-workflow-definitions"></a>Korzystanie z definicji przepływu pracy XAML

Aby utworzyć definicję przepływu pracy dla serializacji, <xref:System.Activities.ActivityBuilder> używana jest Klasa. Tworzenie programu <xref:System.Activities.ActivityBuilder> jest bardzo podobne do <xref:System.Activities.DynamicActivity>tworzenia. Wszystkie żądane argumenty są określone i są konfigurowane działania, które stanowią zachowanie. W poniższym przykładzie `Add` jest tworzone działanie, które przyjmuje dwa argumenty wejściowe, dodaje je razem i zwraca wynik. Ponieważ to działanie zwraca wynik, używana jest Klasa <xref:System.Activities.ActivityBuilder%601> generyczna.

[!code-csharp[CFX_WorkflowApplicationExample#41](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#41)]

Każde wystąpienie reprezentuje jeden z argumentów wejściowych dla przepływu pracy, <xref:System.Activities.ActivityBuilder.Implementation%2A> a zawiera działania, które tworzą logikę przepływu pracy. <xref:System.Activities.DynamicActivityProperty> Należy zauważyć, że wyrażenia r-Value w tym przykładzie są Visual Basic Expressions. Wyrażenia lambda nie można serializować do języka XAML <xref:System.Activities.Expressions.ExpressionServices.Convert%2A> , chyba że jest używany. Jeśli serializowane przepływy pracy mają być otwierane lub edytowane w Projektancie przepływu pracy, należy użyć wyrażeń Visual Basic. Aby uzyskać więcej informacji, zobacz [Tworzenie przepływów pracy, działań i wyrażeń przy użyciu kodu](authoring-workflows-activities-and-expressions-using-imperative-code.md)bezwzględnego.

Aby serializować definicję przepływu pracy reprezentowanego przez <xref:System.Activities.ActivityBuilder> wystąpienie do języka XAML, <xref:System.Activities.XamlIntegration.ActivityXamlServices> Użyj polecenia do <xref:System.Xaml.XamlWriter>utworzenia, a następnie <xref:System.Xaml.XamlServices> Użyj polecenia, aby serializować definicję przepływu pracy <xref:System.Xaml.XamlWriter>przy użyciu. <xref:System.Activities.XamlIntegration.ActivityXamlServices>ma metody mapowania <xref:System.Activities.ActivityBuilder> wystąpień do i z XAML oraz ładowania przepływów pracy XAML i <xref:System.Activities.DynamicActivity> zwracania, które mogą być wywoływane. W poniższym przykładzie <xref:System.Activities.ActivityBuilder> wystąpienie z poprzedniego przykładu jest serializowane do ciągu i zapisywane w pliku.

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

Aby załadować serializowany przepływ pracy, użyj <xref:System.Activities.XamlIntegration.ActivityXamlServices> <xref:System.Activities.XamlIntegration.ActivityXamlServices.Load%2A> metody. Spowoduje to przedefiniowanie serializowanej definicji przepływu pracy <xref:System.Activities.DynamicActivity> i zwrócenie, która reprezentuje definicję przepływu pracy. Należy pamiętać, że kod XAML nie jest deserializowany do momentu <xref:System.Activities.Activity.CacheMetadata%2A> wywołania w treści <xref:System.Activities.DynamicActivity> procesu walidacji. Jeśli walidacja nie jest jawnie wywoływana, jest wykonywana po wywołaniu przepływu pracy. Jeśli definicja przepływu pracy XAML jest nieprawidłowa, <xref:System.ArgumentException> zostanie zgłoszony wyjątek. Wszystkie wyjątki zgłoszone <xref:System.Activities.Activity.CacheMetadata%2A> przez funkcję ucieczki z <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A> wywołania do i muszą być obsługiwane przez wywołującego. W poniższym przykładzie serializowany przepływ pracy z poprzedniego przykładu jest ładowany i wywoływany przy użyciu <xref:System.Activities.WorkflowInvoker>.

[!code-csharp[CFX_WorkflowApplicationExample#43](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#43)]

Po wywołaniu tego przepływu pracy następujące dane wyjściowe są wyświetlane w konsoli programu.

**25 + 15**\
**40**

> [!NOTE]
> Aby uzyskać więcej informacji na temat wywoływania przepływów pracy za pomocą argumentów wejściowych i wyjściowych, zobacz <xref:System.Activities.WorkflowInvoker.Invoke%2A> [using WorkflowInvoker and WorkflowApplication](using-workflowinvoker-and-workflowapplication.md) i.

Jeśli serializowany przepływ pracy C# zawiera wyrażenia, wówczas <xref:System.Activities.XamlIntegration.ActivityXamlServicesSettings> wystąpienie z ustawioną `true` jego <xref:System.Activities.XamlIntegration.ActivityXamlServicesSettings.CompileExpressions%2A> właściwością <xref:System.NotSupportedException> musi być przesyłane jako parametr do <xref:System.Activities.XamlIntegration.ActivityXamlServices.Load%2A?displayProperty=nameWithType>, w przeciwnym razie zostanie wygenerowany komunikat podobny do następujących: **Typ działania Expression "CSharpValue" 1 wymaga kompilacji, aby można było ją uruchomić.  Upewnij się, że przepływ pracy został skompilowany.**

```csharp
ActivityXamlServicesSettings settings = new ActivityXamlServicesSettings
{
    CompileExpressions = true
};

DynamicActivity<int> wf = ActivityXamlServices.Load(new StringReader(serializedAB), settings) as DynamicActivity<int>;
```

Aby uzyskać więcej informacji, [ C# ](csharp-expressions.md)zobacz Expressions.

Można także załadować seryjną definicję przepływu pracy do <xref:System.Activities.ActivityBuilder> wystąpienia przy <xref:System.Activities.XamlIntegration.ActivityXamlServices> <xref:System.Activities.XamlIntegration.ActivityXamlServices.CreateBuilderReader%2A> użyciu metody. Po załadowaniu serializowanego przepływu pracy do <xref:System.Activities.ActivityBuilder> wystąpienia można go sprawdzić i zmodyfikować. Jest to przydatne w przypadku autorów projektanta niestandardowego przepływu pracy i oferuje mechanizm zapisywania i ponownego ładowania definicji przepływu pracy podczas procesu projektowania. W poniższym przykładzie załadowano seryjną definicję przepływu pracy z poprzedniego przykładu, a jej właściwości są kontrolowane.

[!code-csharp[CFX_WorkflowApplicationExample#44](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#44)]
