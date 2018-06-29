### <a name="wpf-datatemplate-elements-are-now-visible-to-uia"></a>Elementy WPF DataTemplate teraz są widoczne dla funkcją UIA

|   |   |
|---|---|
|Szczegóły|Wcześniej <xref:System.Windows.DataTemplate?displayProperty=name> elementy były widoczne dla automatyzacji interfejsu użytkownika. Począwszy od 4.5 automatyzacji interfejsu użytkownika wykrywa te elementy. Jest to użyteczne w wielu przypadkach, ale mogą być dzielone testów, które są zależne od drzew funkcją UIA niezawierający <xref:System.Windows.DataTemplate?displayProperty=name> elementów.|
|Sugestia|Testy automatyzacji interfejsu użytkownika dla tej aplikacji może być konieczne zaktualizowane na wypadek drzewa funkcją UIA obecnie wcześniej niewidoczne <xref:System.Windows.DataTemplate?displayProperty=name> elementów. Na przykład testy, które oczekują niektóre elementy obok siebie może teraz zaistnieć oczekiwać wcześniej niewidocznych elementów funkcją UIA między. Lub testy, które opierają się na niektórych liczby lub indeksów dla elementów funkcją UIA może być konieczne zaktualizowane o nowe wartości.|
|Zakres|Krawędź|
|Wersja|4.5|
|Typ|środowisko uruchomieniowe|
|Dotyczy interfejsów API|<ul><li><xref:System.Windows.DataTemplate.%23ctor?displayProperty=nameWithType></li><li><xref:System.Windows.DataTemplate.%23ctor(System.Object)?displayProperty=nameWithType></li></ul>|

