---
title: Usuwanie stanu widoku, który Projektant dodaje do pliku XAML — WF
ms.date: 03/30/2017
ms.assetid: a801ce22-8699-483c-a392-7bb3834aae4f
ms.openlocfilehash: f431275140e821aa5ec4d2235322f06be87d5ee2
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74715622"
---
# <a name="removing-the-view-state-the-designer-adds-to-an-xaml-file"></a>Usuwanie stanu widoku, który Projektant dodaje do pliku XAML

Ten przykład pokazuje, jak utworzyć klasę, która dziedziczy po <xref:System.Xaml.XamlWriter> i usuwa stan widoku z pliku XAML. System Windows Projektant przepływu pracy zapisuje informacje w dokumencie XAML, który jest znany jako stan widoku. Stan widoku odwołuje się do informacji wymaganych w czasie projektowania, takich jak pozycjonowanie układu, które nie są wymagane w czasie wykonywania. Projektant przepływu pracy wstawia te informacje do dokumentu XAML w trakcie jego edycji. Projektant przepływu pracy zapisuje stan widoku w pliku XAML z atrybutem `mc:Ignorable`, więc te informacje nie zostaną załadowane, gdy środowisko uruchomieniowe załaduje plik XAML. Ten przykład pokazuje, jak utworzyć klasę, która usuwa informacje o stanie widoku podczas przetwarzania węzłów XAML.

## <a name="discussion"></a>Dyskusji

Ten przykład pokazuje, jak utworzyć niestandardowy moduł zapisujący.

Aby utworzyć niestandardowy składnik zapisywania XAML, Utwórz klasę, która dziedziczy po <xref:System.Xaml.XamlWriter>. Ponieważ moduły zapisujące XAML często są zagnieżdżone, typowe jest śledzenie "wewnętrznego" składnika zapisywania XAML. Te "wewnętrzne" składowe można traktować jako odwołanie do pozostałego stosu autorów XAML, co pozwala na wykonywanie wielu punktów wejścia do pracy, a następnie delegowanie przetwarzania do pozostałej części stosu.

W tym przykładzie istnieje kilka interesujących rzeczy. Jednym z nich jest sprawdzenie, czy element jest zapisywany, pochodzi z przestrzeni nazw projektanta. Należy zauważyć, że spowoduje to również przydzielenie użycia innych typów z przestrzeni nazw projektanta w przepływie pracy.

```csharp
static Boolean IsDesignerAttachedProperty(XamlMember xamlMember)
{
    return xamlMember.IsAttachable &&
        xamlMember.PreferredXamlNamespace.Equals(c_sapNamespaceURI, StringComparison.OrdinalIgnoreCase);
}

const String c_sapNamespaceURI = "http://schemas.microsoft.com/netfx/2009/xaml/activities/presentation";

// The next item of interest is the constructor, where the utilization of the inner XAML writer is seen.
public ViewStateCleaningWriter(XamlWriter innerWriter)
{
    this.InnerWriter = innerWriter;
    this.MemberStack = new Stack<XamlMember>();
}

XamlWriter InnerWriter {get; set; }
Stack<XamlMember> MemberStack {get; set; }
```

Powoduje to również utworzenie stosu elementów członkowskich XAML, które są używane podczas przechodzenia przez strumień węzła. Pozostała część pracy tego przykładu jest w dużym stopniu zawarta w metodzie `WriteStartMember`.

```csharp
public override void WriteStartMember(XamlMember xamlMember)
{
    MemberStack.Push(xamlMember);

    if (IsDesignerAttachedProperty(xamlMember))
    {
        m_attachedPropertyDepth++;
    }

    if (m_attachedPropertyDepth > 0)
    {
        return;
    }

    InnerWriter.WriteStartMember(xamlMember);
}
```

Kolejne metody, a następnie sprawdzają, czy nadal znajdują się w kontenerze Stanów widoku, a jeśli tak, zwracają i nie przekazują węzła w dół stosu składnika zapisywania.

```csharp
public override void WriteValue(Object value)
{
    if (m_attachedPropertyDepth > 0)
    {
        return;
    }

    InnerWriter.WriteValue(value);
}
```

Aby użyć niestandardowego składnika zapisywania XAML, należy łańcuchować go razem w stosie modułów zapisujących XAML. Poniższy kod przedstawia, jak można go użyć.

```csharp
XmlWriterSettings writerSettings = new XmlWriterSettings {  Indent = true };
XmlWriter xmlWriter = XmlWriter.Create(File.OpenWrite(args[1]), writerSettings);
XamlXmlWriter xamlWriter = new XamlXmlWriter(xmlWriter, new XamlSchemaContext());
XamlServices.Save(new ViewStateCleaningWriter(ActivityXamlServices.CreateBuilderWriter(xamlWriter)), ab);
```

## <a name="to-use-this-sample"></a>Aby użyć tego przykładu

1. Za pomocą programu Visual Studio 2010 Otwórz plik rozwiązania ViewStateCleaningWriter. sln.

2. Otwórz wiersz polecenia i przejdź do katalogu, w którym utworzono plik ViewStageCleaningWriter. exe.

3. Uruchom ViewStateCleaningWriter. exe w pliku Workflow1. XAML.

   Składnia dla pliku wykonywalnego jest pokazana w poniższym przykładzie.

   ```console
   ViewStateCleaningWriter.exe [input file] [output file]
   ```

   Spowoduje to wyjście z pliku XAML w celu \[pliku], który ma wszystkie usunięte informacje o stanie widoku.

> [!NOTE]
> W przypadku przepływu pracy <xref:System.Activities.Statements.Sequence> są usuwane różne wskazówki dotyczące wirtualizacji. Powoduje to, że projektant będzie ponownie obliczał układ przy następnym załadowaniu. Gdy użyjesz tego przykładu dla <xref:System.Activities.Statements.Flowchart>, wszystkie informacje o rozłożeniu i trasie są usuwane i po następnym załadowaniu do projektanta wszystkie działania są układane po lewej stronie ekranu.

## <a name="to-create-a-sample-xaml-file-for-use-with-this-sample"></a>Aby utworzyć przykładowy plik XAML do użycia z tym przykładem

1. Otwórz program Visual Studio 2010.

2. Utwórz nową aplikację konsoli przepływu pracy.

3. Przeciągnij i upuść kilka działań na kanwę

4. Zapisz plik XAML przepływu pracy.

5. Sprawdź plik XAML, aby wyświetlić właściwości widoku dołączonego stanu.

> [!IMPORTANT]
> Przykłady mogą być już zainstalowane na komputerze. Przed kontynuowaniem Wyszukaj następujący katalog (domyślny).
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> Jeśli ten katalog nie istnieje, przejdź do [przykładów Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) dla .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) , aby pobrać wszystkie próbki Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)]. Ten przykład znajduje się w następującym katalogu.
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Designer\ViewStateCleaningWriter`
