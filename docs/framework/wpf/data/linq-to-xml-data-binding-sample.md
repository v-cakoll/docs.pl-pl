---
title: Przykład powiązania danych LINQ to XML
ms.date: 10/22/2019
ms.topic: sample
helpviewer_keywords:
- linq to xml data binding sample
ms.openlocfilehash: aac814e4768a863a93e69e34cd18c941a9b35c89
ms.sourcegitcommit: 82f94a44ad5c64a399df2a03fa842db308185a76
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/25/2019
ms.locfileid: "72920938"
---
# <a name="linq-to-xml-data-binding-sample"></a>Przykład powiązania danych LINQ to XML

W tym artykule opisano przykład elementu LinqToXmlDataBinding —, aplikację Windows Presentation Foundation (WPF), która wiąże składniki interfejsu użytkownika z osadzonym źródłem danych XML.

## <a name="overview"></a>Omówienie

Przykład elementu LinqToXmlDataBinding — jest aplikacją Windows Presentation Foundation (WPF), która zawiera C# pliki źródłowe XAML i. Osadzony dokument XML definiuje listę książek. Aplikacja umożliwia użytkownikowi wyświetlanie, Dodawanie, usuwanie i edytowanie wpisów książki.

Istnieją dwa podstawowe pliki źródłowe:

- [Kod źródłowy L2DBForm. XAML](l2dbform-xaml-source-code.md) zawiera kod deklaracji XAML dla interfejsu użytkownika okna głównego. Zawiera również sekcję zasobów okna, która definiuje dostawcę danych i osadzony dokument XML dla list książek.

- [L2DBForm.XAML.cs](l2dbform-xaml-cs-source-code.md) zawiera metody inicjowania i obsługi zdarzeń SKOJARZONE z interfejsem użytkownika.

Okno główne jest podzielone na następujące cztery pionowe sekcje interfejsu użytkownika:

- **Kod XML** Wyświetla pierwotne źródło XML listy osadzonych książek.

- **Lista książek** wyświetla wpisy książki jako tekst standardowy i umożliwia użytkownikowi wybranie i usunięcie poszczególnych wpisów.

- **Edycja wybranej książki** umożliwia użytkownikowi edytowanie wartości skojarzonych z aktualnie wybranym wpisem książki.

- **Dodawanie nowej książki** umożliwia tworzenie nowych wpisów książki na podstawie wartości wprowadzonych przez użytkownika.

## <a name="run-the-sample"></a>Uruchamianie przykładu

W tej sekcji pokazano, jak utworzyć i skompilować projekt elementu LinqToXmlDataBinding — w programie Visual Studio oraz jak uruchomić utworzoną aplikację elementu LinqToXmlDataBinding — Windows Presentation Foundation (WPF).

### <a name="create-the-project"></a>Utwórz projekt

1. Otwórz program Visual Studio i Utwórz C# **aplikację WPF** o nazwie **elementu LinqToXmlDataBinding —** .

   Projekt powinien kierować do .NET Framework 3,5 (lub nowszego).

1. Jeśli jeszcze nie istnieje, Dodaj odwołania do projektu dla następujących zestawów .NET:

    - System.Data
    - System. Data. DataSetExtensions
    - System.Xml
    - System.Xml

1. Skompiluj rozwiązanie, naciskając klawisz **Ctrl** +**SHIFT** +**B**, a następnie uruchom go, naciskając klawisz **F5**.

   Projekt powinien zostać skompilowany bez błędów i uruchomiony jako ogólna aplikacja WPF.

### <a name="add-code"></a>Dodaj kod

1. W **Eksplorator rozwiązań**Zmień nazwę pliku źródłowego **window1. XAML** na **L2XDBForm. XAML**.

   Window1.xaml.cs pliku źródłowego zależnego jest automatycznie zmieniana na L2XDBForm.xaml.cs.

1. Zamień kod źródłowy znaleziony w pliku **L2XDBForm. XAML** na [kod źródłowy kod źródłowy L2DBForm. XAML](l2dbform-xaml-source-code.md). Użyj widoku źródła XAML do pracy z tym plikiem.

1. Podobnie zastąp źródło w **L2XDBForm.XAML.cs** z [kodem źródłowym L2DBForm.XAML.cs](l2dbform-xaml-cs-source-code.md).

1. W pliku **App. XAML**Zamień wszystkie wystąpienia ciągu **window1. XAML** na **L2XDBForm. XAML**.

1. Skompiluj rozwiązanie, naciskając klawisz **Ctrl** +**SHIFT** +**B**.

### <a name="run-the-app"></a>Uruchamianie aplikacji

Aplikacja elementu LinqToXmlDataBinding — umożliwia użytkownikowi wyświetlanie listy książek przechowywanych jako osadzony element XML i manipulowanie nimi. Uruchom aplikację, naciskając klawisz **F5** (Rozpocznij debugowanie) lub **Ctrl**+**F5** (Rozpocznij bez debugowania).

Zostanie wyświetlone okno programu z tytułem **powiązania danych WPF przy użyciu LINQ to XML** .

W górnej części interfejsu użytkownika jest wyświetlany nieprzetworzony **kod XML** , który reprezentuje listę książek. Jest ona wyświetlana przy użyciu kontrolki <xref:System.Windows.Controls.TextBlock> WPF, która nie umożliwia interakcji za pośrednictwem myszy lub klawiatury.

Druga sekcja pionowa z etykietą **lista książek**zawiera książki jako listę uporządkowaną jako zwykły tekst. Używa kontrolki <xref:System.Windows.Controls.ListBox>, która umożliwia wybór za pośrednictwem myszy lub klawiatury.

### <a name="add-and-delete-books"></a>Dodawanie i usuwanie książek

Aby dodać nową książkę do listy, wprowadź wartości w polu **Identyfikator** i **wartość** <xref:System.Windows.Controls.TextBox> kontrolki w ostatniej sekcji, **Dodaj nową książkę**, a następnie wybierz pozycję **Dodaj książkę**. Książka jest dołączana do listy w listach książki i XML. Ten program nie weryfikuje wartości wejściowych.

Aby usunąć istniejącą książkę z listy, wybierz ją w sekcji **lista książek** , a następnie wybierz pozycję **Usuń wybraną książkę**. Wpis książki jest usuwany z list książek i nieprzetworzonych źródeł XML.

### <a name="edit-a-book-entry"></a>Edytuj wpis książki

1. Wybierz wpis książki w drugiej sekcji **listy książek** .

   Bieżące wartości są wyświetlane w sekcji **Edytuj wybraną książkę** .

1. Edytuj wartości przy użyciu klawiatury. Gdy tylko formant <xref:System.Windows.Controls.TextBox> utraci fokus, zmiany są automatycznie propagowane do listy źródłowej XML i książki.
