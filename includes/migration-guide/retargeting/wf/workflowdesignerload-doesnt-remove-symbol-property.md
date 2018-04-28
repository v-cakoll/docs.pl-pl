### <a name="workflowdesignerload-doesnt-remove-symbol-property"></a>WorkflowDesigner.Load nie powoduje usunięcia właściwość symbol

|   |   |
|---|---|
|Szczegóły|Podczas określania wartości docelowej platformy .NET Framework 4.5 w Projektancie przepływów pracy i ładowanie ponownie hostowanej 3,5 przepływu pracy z <xref:System.Activities.Presentation.WorkflowDesigner.Load> metody <xref:System.Xaml.XamlDuplicateMemberException?displayProperty=name> jest generowany podczas zapisywania przepływ pracy.|
|Sugestia|Ta usterka tylko w sytuacji, gdy przeznaczonych dla platformy .NET Framework 4.5 w Projektancie przepływów pracy, dlatego może być działał wokół przez ustawienie <code>WorkflowDesigner.Context.Services.GetService&lt;DesignerConfigurationService&gt;().TargetFrameworkName</code> do 4.0 .NET Framework.Alternatively, można uniknąć problemu, przy użyciu <xref:System.Activities.Presentation.WorkflowDesigner.Load(System.String)> metody w celu załadowania przepływu pracy, zamiast <xref:System.Activities.Presentation.WorkflowDesigner.Load>.|
|Zakres|Główne|
|Wersja|4.5|
|Typ|Przekierowania|
|Dotyczy interfejsów API|<ul><li><xref:System.Activities.Presentation.WorkflowDesigner.Load?displayProperty=nameWithType></li></ul>|

