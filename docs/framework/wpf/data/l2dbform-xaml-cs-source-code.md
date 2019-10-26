---
title: Kod źródłowy L2DBForm.xaml.cs
ms.date: 10/22/2019
ms.topic: sample
ms.openlocfilehash: 882699a76eab3c291cd92c298287bc5d28fb08e1
ms.sourcegitcommit: 82f94a44ad5c64a399df2a03fa842db308185a76
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/25/2019
ms.locfileid: "72920861"
---
# <a name="l2dbformxamlcs-source-code"></a><span data-ttu-id="e5a43-102">Kod źródłowy L2DBForm.xaml.cs</span><span class="sxs-lookup"><span data-stu-id="e5a43-102">L2DBForm.xaml.cs source code</span></span>

<span data-ttu-id="e5a43-103">Ta strona zawiera zawartość i Opis kodu C# źródłowego w pliku *L2DBForm.XAML.cs*.</span><span class="sxs-lookup"><span data-stu-id="e5a43-103">This page contains the contents and description of the C# source code in the file *L2DBForm.xaml.cs*.</span></span> <span data-ttu-id="e5a43-104">Klasa częściowa L2XDBForm znajdująca się w tym pliku może zostać podzielona na trzy sekcje logiczne: elementy członkowskie danych i przycisk `OnRemove` i `OnAddBook` kliknij pozycję Programy obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="e5a43-104">The L2XDBForm partial class contained in this file can be divided into three logical sections: data members and the `OnRemove` and `OnAddBook` button click event handlers.</span></span>

## <a name="data-members"></a><span data-ttu-id="e5a43-105">Elementy członkowskie danych</span><span class="sxs-lookup"><span data-stu-id="e5a43-105">Data members</span></span>

<span data-ttu-id="e5a43-106">Dwa prywatne elementy członkowskie danych są używane do kojarzenia tej klasy z zasobami okna używanymi w *kod źródłowy L2DBForm. XAML*.</span><span class="sxs-lookup"><span data-stu-id="e5a43-106">Two private data members are used to associate this class to the window resources used in *L2DBForm.xaml*.</span></span>

- <span data-ttu-id="e5a43-107">Zmienna przestrzeni nazw `myBooks` została zainicjowana, aby `"http://www.mybooks.com"`.</span><span class="sxs-lookup"><span data-stu-id="e5a43-107">The namespace variable `myBooks` is initialized to `"http://www.mybooks.com"`.</span></span>

- <span data-ttu-id="e5a43-108">`bookList` elementu członkowskiego jest inicjowana w konstruktorze do ciągu CDATA w *kod źródłowy L2DBForm. XAML* z następującym wierszem:</span><span class="sxs-lookup"><span data-stu-id="e5a43-108">The member `bookList` is initialized in the constructor to the CDATA string in *L2DBForm.xaml* with the following line:</span></span>

    ```csharp
    bookList = (XElement)((ObjectDataProvider)Resources["LoadedBooks"]).Data;
    ```

## <a name="onaddbook-event-handler"></a><span data-ttu-id="e5a43-109">Procedura obsługi zdarzeń OnAddBook</span><span class="sxs-lookup"><span data-stu-id="e5a43-109">OnAddBook event handler</span></span>

<span data-ttu-id="e5a43-110">Ta metoda zawiera trzy następujące instrukcje:</span><span class="sxs-lookup"><span data-stu-id="e5a43-110">This method contains the following three statements:</span></span>

- <span data-ttu-id="e5a43-111">Pierwsza Instrukcja warunkowa służy do sprawdzania poprawności danych wejściowych.</span><span class="sxs-lookup"><span data-stu-id="e5a43-111">The first conditional statement is used for input validation.</span></span>

- <span data-ttu-id="e5a43-112">Druga instrukcja tworzy nowe <xref:System.Xml.Linq.XElement> z wartości ciągów wprowadzonych przez użytkownika w sekcji **Dodaj nowy** interfejs użytkownika książki (UI).</span><span class="sxs-lookup"><span data-stu-id="e5a43-112">The second statement creates a new <xref:System.Xml.Linq.XElement> from the string values the user entered in the **Add New Book** user interface (UI) section.</span></span>

- <span data-ttu-id="e5a43-113">Ostatnia instrukcja dodaje nowy element książki do dostawcy danych w *kod źródłowy L2DBForm. XAML*.</span><span class="sxs-lookup"><span data-stu-id="e5a43-113">The last statement adds this new book element to the data provider in *L2DBForm.xaml*.</span></span> <span data-ttu-id="e5a43-114">W związku z tym dynamiczne powiązanie danych automatycznie zaktualizuje interfejs użytkownika przy użyciu tego nowego elementu; nie jest wymagany żaden dodatkowy kod dostarczony przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="e5a43-114">Consequently, dynamic data binding will automatically update the UI with this new item; no extra user-supplied code is required.</span></span>

## <a name="onremove-event-handler"></a><span data-ttu-id="e5a43-115">Procedura obsługi zdarzeń OnRemove</span><span class="sxs-lookup"><span data-stu-id="e5a43-115">OnRemove event handler</span></span>

<span data-ttu-id="e5a43-116">Procedura obsługi `OnRemove` jest bardziej skomplikowana niż obsługa `OnAddBook` z dwóch przyczyn.</span><span class="sxs-lookup"><span data-stu-id="e5a43-116">The `OnRemove` handler is more complicated than the `OnAddBook` handler for two reasons.</span></span> <span data-ttu-id="e5a43-117">Po pierwsze, ponieważ nieprzetworzony kod XML zawiera zachowany biały znak, należy również usunąć pasujące znaki nowego wiersza z wpisem książki.</span><span class="sxs-lookup"><span data-stu-id="e5a43-117">First, because the raw XML contains preserved white space, matching newlines must also be removed with the book entry.</span></span> <span data-ttu-id="e5a43-118">Po drugie, jako wygoda, wybór, który został usunięty z usuniętego elementu, jest resetowany do poprzedniej z nich na liście.</span><span class="sxs-lookup"><span data-stu-id="e5a43-118">Second, as a convenience, the selection, which was on the deleted item, is reset to the previous one in the list.</span></span>

<span data-ttu-id="e5a43-119">Jednak podstawowe zadania usuwania wybranego elementu księgi są wykonywane tylko przez dwie instrukcje:</span><span class="sxs-lookup"><span data-stu-id="e5a43-119">However, the core work of removing the selected book item is accomplished by only two statements:</span></span>

- <span data-ttu-id="e5a43-120">Najpierw zostanie pobrany element Book skojarzony z aktualnie wybranym elementem w polu listy:</span><span class="sxs-lookup"><span data-stu-id="e5a43-120">First, the book element associated with the currently selected item in the list box is retrieved:</span></span>

    ```csharp
    XElement selBook = (XElement)lbBooks.SelectedItem;
    ```

- <span data-ttu-id="e5a43-121">Następnie ten element zostanie usunięty z dostawcy danych:</span><span class="sxs-lookup"><span data-stu-id="e5a43-121">Then, this element is deleted from the data provider:</span></span>

    ```csharp
    selBook.Remove();
    ```

<span data-ttu-id="e5a43-122">Po ponownym rozwiązaniu danych dynamicznych gwarantuje, że interfejs użytkownika programu jest automatycznie aktualizowany.</span><span class="sxs-lookup"><span data-stu-id="e5a43-122">Again, dynamic data binding assures that the program's UI is automatically updated.</span></span>

## <a name="example"></a><span data-ttu-id="e5a43-123">Przykład</span><span class="sxs-lookup"><span data-stu-id="e5a43-123">Example</span></span>

### <a name="code"></a><span data-ttu-id="e5a43-124">Kod</span><span class="sxs-lookup"><span data-stu-id="e5a43-124">Code</span></span>

```csharp
using System;
using System.Linq;
using System.Collections;
using System.Collections.Generic;
using System.Diagnostics;
using System.Text;
using System.Windows;
using System.Windows.Controls;
using System.Windows.Data;
using System.Windows.Input;
using System.Xml;
using System.Xml.Linq;

namespace LinqToXmlDataBinding {
    /// <summary>
    /// Interaction logic for L2XDBForm.xaml
    /// </summary>

    public partial class L2XDBForm : System.Windows.Window
    {
        XNamespace mybooks = "http://www.mybooks.com";
        XElement bookList;

        public L2XDBForm()
        {
            InitializeComponent();
            bookList = (XElement)((ObjectDataProvider)Resources["LoadedBooks"]).Data;
        }

        void OnRemoveBook(object sender, EventArgs e)
        {
            int index = lbBooks.SelectedIndex;
            if (index < 0) return;

            XElement selBook = (XElement)lbBooks.SelectedItem;
            //Get next node before removing element.
            XNode nextNode = selBook.NextNode;
            selBook.Remove();

            //Remove any matching newline node.
            if (nextNode != null && nextNode.ToString().Trim().Equals(""))
            { nextNode.Remove(); }

            //Set selected item.
            if (lbBooks.Items.Count > 0)
            {  lbBooks.SelectedItem = lbBooks.Items[index > 0 ? index - 1 : 0]; }
        }

        void OnAddBook(object sender, EventArgs e)
        {
            if (String.IsNullOrEmpty(tbAddID.Text) ||
                String.IsNullOrEmpty(tbAddValue.Text))
            {
                MessageBox.Show("Please supply both a Book ID and a Value!", "Entry Error!");
                return;
            }
            XElement newBook = new XElement(
                                mybooks + "book",
                                new XAttribute("id", tbAddID.Text),
                                tbAddValue.Text);
            bookList.Add("  ", newBook, "\r\n");
        }
    }
}
```

### <a name="comments"></a><span data-ttu-id="e5a43-125">Komentarze</span><span class="sxs-lookup"><span data-stu-id="e5a43-125">Comments</span></span>

<span data-ttu-id="e5a43-126">Dla skojarzonego źródła XAML dla tych programów obsługi zobacz [kod źródłowy kod źródłowy L2DBForm. XAML](l2dbform-xaml-source-code.md).</span><span class="sxs-lookup"><span data-stu-id="e5a43-126">For the associated XAML source for these handlers, see [L2DBForm.xaml source code](l2dbform-xaml-source-code.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="e5a43-127">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e5a43-127">See also</span></span>

- [<span data-ttu-id="e5a43-128">Przewodnik: elementu LinqToXmlDataBinding — przykład</span><span class="sxs-lookup"><span data-stu-id="e5a43-128">Walkthrough: LinqToXmlDataBinding example</span></span>](linq-to-xml-data-binding-sample.md)
- [<span data-ttu-id="e5a43-129">Kod źródłowy L2DBForm.xaml</span><span class="sxs-lookup"><span data-stu-id="e5a43-129">L2DBForm.xaml source code</span></span>](l2dbform-xaml-source-code.md)
