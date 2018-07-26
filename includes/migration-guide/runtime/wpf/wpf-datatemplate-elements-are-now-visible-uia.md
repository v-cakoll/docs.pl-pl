### <a name="wpf-datatemplate-elements-are-now-visible-to-uia"></a>Elementów WPF DataTemplate są teraz widoczne dla automatyzacji interfejsu użytkownika

|   |   |
|---|---|
|Szczegóły|Wcześniej <xref:System.Windows.DataTemplate?displayProperty=name> elementy są niewidoczne dla automatyzacji interfejsu użytkownika. Począwszy od 4.5 automatyzacji interfejsu użytkownika wykryje te elementy. Jest to przydatne w wielu przypadkach, ale może przerwać testy, które są zależne od drzewa automatyzacji interfejsu użytkownika nie zawiera <xref:System.Windows.DataTemplate?displayProperty=name> elementów.|
|Sugestia|Testy automatyzacji interfejsu użytkownika dla tej aplikacji może być konieczne aktualizowane na wypadek drzewa UIA, w tym teraz wcześniej niewidoczne <xref:System.Windows.DataTemplate?displayProperty=name> elementów. Na przykład testy, które oczekują niektóre elementy pod kątem się obok siebie może teraz trzeba oczekiwać wcześniej niewidocznych elementów automatyzacji interfejsu użytkownika między. Lub testów, które zależą od niektórych liczby ani indeksów dla elementów automatyzacji interfejsu użytkownika może być konieczne zaktualizowane z nowymi wartościami.|
|Zakres|Krawędź|
|Wersja|4.5|
|Typ|Środowisko uruchomieniowe|
|Dotyczy interfejsów API|<ul><li><xref:System.Windows.DataTemplate.%23ctor?displayProperty=nameWithType></li><li><xref:System.Windows.DataTemplate.%23ctor(System.Object)?displayProperty=nameWithType></li></ul>|

