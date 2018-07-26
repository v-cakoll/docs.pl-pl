### <a name="workflowdesignerload-doesnt-remove-symbol-property"></a>WorkflowDesigner.Load nie powoduje usunięcia właściwości symboli

|   |   |
|---|---|
|Szczegóły|Podczas określania wartości docelowej programu .NET Framework 4.5 w Projektancie przepływu pracy i ładowanie ponownie hostowanej 3,5 przepływu pracy przy użyciu <xref:System.Activities.Presentation.WorkflowDesigner.Load> metody <xref:System.Xaml.XamlDuplicateMemberException?displayProperty=name> zgłaszany podczas zapisywania przepływu pracy.|
|Sugestia|Ta usterka wyłącznie w sytuacji, gdy przeznaczone dla .NET Framework 4.5 w Projektancie przepływu pracy, dzięki czemu możesz pracować nad całym, ustawiając <code>WorkflowDesigner.Context.Services.GetService&lt;DesignerConfigurationService&gt;().TargetFrameworkName</code> do wersji 4.0 Framework.Alternatively .NET, można uniknąć problemu, przy użyciu <xref:System.Activities.Presentation.WorkflowDesigner.Load(System.String)> metodę, aby załadować przepływu pracy, zamiast <xref:System.Activities.Presentation.WorkflowDesigner.Load>.|
|Zakres|Główne|
|Wersja|4.5|
|Typ|Trwa przekierowywanie|
|Dotyczy interfejsów API|<ul><li><xref:System.Activities.Presentation.WorkflowDesigner.Load?displayProperty=nameWithType></li></ul>|

