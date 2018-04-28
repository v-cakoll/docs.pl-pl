### <a name="some-workflow-drag-and-drop-apis-are-obsolete"></a>Niektórych interfejsów API przeciągania i upuszczania przepływu pracy są nieaktualne

|   |   |
|---|---|
|Szczegóły|Ten interfejs API przeciągania i upuszczania przepływu pracy jest przestarzały i jeśli aplikacja zostanie odtworzony przed 4.5 spowoduje ostrzeżeń kompilatora.|
|Sugestia|Nowe <xref:System.Activities.Presentation.DragDropHelper?displayProperty=name> interfejsów API, która obsługuje operacje z wielu obiektów należy użyć. Alternatywnie można pominąć ostrzeżenia kompilacji lub można uniknąć za pomocą starszego kompilatora. Interfejsy API są wciąż obsługiwane.|
|Zakres|Pomocnicza|
|Wersja|4.5|
|Typ|Przekierowania|
|Dotyczy interfejsów API|<ul><li><xref:System.Activities.Presentation.DragDropHelper.DoDragMove(System.Activities.Presentation.WorkflowViewElement,System.Windows.Point)?displayProperty=nameWithType></li><li><xref:System.Activities.Presentation.DragDropHelper.GetCompositeView(System.Windows.DragEventArgs)?displayProperty=nameWithType></li><li><xref:System.Activities.Presentation.DragDropHelper.GetDraggedModelItem(System.Windows.DragEventArgs)?displayProperty=nameWithType></li><li><xref:System.Activities.Presentation.DragDropHelper.GetDroppedObject(System.Windows.DependencyObject,System.Windows.DragEventArgs,System.Activities.Presentation.EditingContext)?displayProperty=nameWithType></li></ul>|

