---
title: 'Porady: tworzenie prywatnej kolekcji czcionek'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- private font collections [Windows Forms], creating
- fonts [Windows Forms], creating private collections
ms.assetid: 6533d5e5-a8dc-4b76-9fc4-3bf75c8b9212
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 3016fb9a1b1d8466137bcaddb0b885c02c399baf
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-a-private-font-collection"></a><span data-ttu-id="e4d7c-102">Porady: tworzenie prywatnej kolekcji czcionek</span><span class="sxs-lookup"><span data-stu-id="e4d7c-102">How to: Create a Private Font Collection</span></span>
<span data-ttu-id="e4d7c-103"><xref:System.Drawing.Text.PrivateFontCollection> Klasa dziedziczy <xref:System.Drawing.Text.FontCollection> abstrakcyjnej klasy podstawowej.</span><span class="sxs-lookup"><span data-stu-id="e4d7c-103">The <xref:System.Drawing.Text.PrivateFontCollection> class inherits from the <xref:System.Drawing.Text.FontCollection> abstract base class.</span></span> <span data-ttu-id="e4d7c-104">Można użyć <xref:System.Drawing.Text.PrivateFontCollection> obiektu przechowywać zestawu czcionek specjalnie dla aplikacji.</span><span class="sxs-lookup"><span data-stu-id="e4d7c-104">You can use a <xref:System.Drawing.Text.PrivateFontCollection> object to maintain a set of fonts specifically for your application.</span></span> <span data-ttu-id="e4d7c-105">Kolekcja prywatnej czcionki mogą obejmować czcionek zainstalowanego systemu, a także czcionek, które nie zostały zainstalowane na komputerze.</span><span class="sxs-lookup"><span data-stu-id="e4d7c-105">A private font collection can include installed system fonts as well as fonts that have not been installed on the computer.</span></span> <span data-ttu-id="e4d7c-106">Aby dodać plik czcionki do kolekcji czcionki prywatnych, należy wywołać <xref:System.Drawing.Text.PrivateFontCollection.AddFontFile%2A> metody <xref:System.Drawing.Text.PrivateFontCollection> obiektu.</span><span class="sxs-lookup"><span data-stu-id="e4d7c-106">To add a font file to a private font collection, call the <xref:System.Drawing.Text.PrivateFontCollection.AddFontFile%2A> method of a <xref:System.Drawing.Text.PrivateFontCollection> object.</span></span>  
  
 <span data-ttu-id="e4d7c-107"><xref:System.Drawing.Text.FontCollection.Families%2A> Właściwość <xref:System.Drawing.Text.PrivateFontCollection> obiektu zawiera tablicę <xref:System.Drawing.FontFamily> obiektów.</span><span class="sxs-lookup"><span data-stu-id="e4d7c-107">The <xref:System.Drawing.Text.FontCollection.Families%2A> property of a <xref:System.Drawing.Text.PrivateFontCollection> object contains an array of <xref:System.Drawing.FontFamily> objects.</span></span>  
  
 <span data-ttu-id="e4d7c-108">Liczba rodziny czcionek w kolekcji prywatnych czcionek nie jest zawsze taka sama jak liczba plików czcionek, które zostały dodane do kolekcji.</span><span class="sxs-lookup"><span data-stu-id="e4d7c-108">The number of font families in a private font collection is not necessarily the same as the number of font files that have been added to the collection.</span></span> <span data-ttu-id="e4d7c-109">Na przykład załóżmy, że pliki ArialBd.tff, Times.tff i TimesBd.tff można dodać do kolekcji.</span><span class="sxs-lookup"><span data-stu-id="e4d7c-109">For example, suppose you add the files ArialBd.tff, Times.tff, and TimesBd.tff to a collection.</span></span> <span data-ttu-id="e4d7c-110">Będzie trzy pliki, ale tylko dwa rodzin w kolekcji ponieważ Times.tff i TimesBd.tff należą do tej samej rodziny.</span><span class="sxs-lookup"><span data-stu-id="e4d7c-110">There will be three files but only two families in the collection because Times.tff and TimesBd.tff belong to the same family.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e4d7c-111">Przykład</span><span class="sxs-lookup"><span data-stu-id="e4d7c-111">Example</span></span>  
 <span data-ttu-id="e4d7c-112">W poniższym przykładzie dodano następujące pliki trzy czcionki do <xref:System.Drawing.Text.PrivateFontCollection> obiektu:</span><span class="sxs-lookup"><span data-stu-id="e4d7c-112">The following example adds the following three font files to a <xref:System.Drawing.Text.PrivateFontCollection> object:</span></span>  
  
-   <span data-ttu-id="e4d7c-113">C:\\*systemroot*\Fonts\Arial.tff (Arial, regularne)</span><span class="sxs-lookup"><span data-stu-id="e4d7c-113">C:\\*systemroot*\Fonts\Arial.tff (Arial, regular)</span></span>  
  
-   <span data-ttu-id="e4d7c-114">C:\\*systemroot*\Fonts\CourBI.tff (Courier New pogrubienie, kursywa)</span><span class="sxs-lookup"><span data-stu-id="e4d7c-114">C:\\*systemroot*\Fonts\CourBI.tff (Courier New, bold italic)</span></span>  
  
-   <span data-ttu-id="e4d7c-115">C:\\*systemroot*\Fonts\TimesBd.tff (razy nowe łacińskich, pogrubione)</span><span class="sxs-lookup"><span data-stu-id="e4d7c-115">C:\\*systemroot*\Fonts\TimesBd.tff (Times New Roman, bold)</span></span>  
  
 <span data-ttu-id="e4d7c-116">Ten kod pobiera tablicę <xref:System.Drawing.FontFamily> obiektów z <xref:System.Drawing.Text.FontCollection.Families%2A> właściwość <xref:System.Drawing.Text.PrivateFontCollection> obiektu.</span><span class="sxs-lookup"><span data-stu-id="e4d7c-116">The code retrieves an array of <xref:System.Drawing.FontFamily> objects from the <xref:System.Drawing.Text.FontCollection.Families%2A> property of the <xref:System.Drawing.Text.PrivateFontCollection> object.</span></span>  
  
 <span data-ttu-id="e4d7c-117">Dla każdego <xref:System.Drawing.FontFamily> obiektu w kolekcji, kod wywołuje <xref:System.Drawing.FontFamily.IsStyleAvailable%2A> metodę, aby określić, czy dostępne są różne style (regularne, pogrubienie, kursywa, pogrubienie, kursywa, podkreślenia i przekreślenia).</span><span class="sxs-lookup"><span data-stu-id="e4d7c-117">For each <xref:System.Drawing.FontFamily> object in the collection, the code calls the <xref:System.Drawing.FontFamily.IsStyleAvailable%2A> method to determine whether various styles (regular, bold, italic, bold italic, underline, and strikeout) are available.</span></span> <span data-ttu-id="e4d7c-118">Argumenty przekazywane do <xref:System.Drawing.FontFamily.IsStyleAvailable%2A> metody są elementami członkowskimi <xref:System.Drawing.FontStyle> wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="e4d7c-118">The arguments passed to the <xref:System.Drawing.FontFamily.IsStyleAvailable%2A> method are members of the <xref:System.Drawing.FontStyle> enumeration.</span></span>  
  
 <span data-ttu-id="e4d7c-119">Jeśli jest dostępna, kombinacja danej rodziny i stylu <xref:System.Drawing.Font> obiekt jest tworzony przy użyciu tej rodziny i stylu.</span><span class="sxs-lookup"><span data-stu-id="e4d7c-119">If a given family/style combination is available, a <xref:System.Drawing.Font> object is constructed using that family and style.</span></span> <span data-ttu-id="e4d7c-120">Pierwszy argument przekazany do <xref:System.Drawing.Font.%23ctor%2A> Konstruktor jest nazwę rodziny czcionek (nie <xref:System.Drawing.FontFamily> obiektów, jak w przypadku innych zmian <xref:System.Drawing.Font.%23ctor%2A> konstruktora).</span><span class="sxs-lookup"><span data-stu-id="e4d7c-120">The first argument passed to the <xref:System.Drawing.Font.%23ctor%2A> constructor is the font family name (not a <xref:System.Drawing.FontFamily> object as is the case for other variations of the <xref:System.Drawing.Font.%23ctor%2A> constructor).</span></span> <span data-ttu-id="e4d7c-121">Po <xref:System.Drawing.Font> konstruowania obiektu, jest przekazywany do <xref:System.Drawing.Graphics.DrawString%2A> metody <xref:System.Drawing.Graphics> klasy do wyświetlenia nazwisko oraz nazwę stylu.</span><span class="sxs-lookup"><span data-stu-id="e4d7c-121">After the <xref:System.Drawing.Font> object is constructed, it is passed to the <xref:System.Drawing.Graphics.DrawString%2A> method of the <xref:System.Drawing.Graphics> class to display the family name along with the name of the style.</span></span>  
  
 <span data-ttu-id="e4d7c-122">Dane wyjściowe następujący kod jest podobny do danych wyjściowych pokazano na poniższej ilustracji.</span><span class="sxs-lookup"><span data-stu-id="e4d7c-122">The output of the following code is similar to the output shown in the following illustration.</span></span>  
  
 <span data-ttu-id="e4d7c-123">![Czcionki tekstu](../../../../docs/framework/winforms/advanced/media/csfontstext7.png "csfontstext7")</span><span class="sxs-lookup"><span data-stu-id="e4d7c-123">![Fonts Text](../../../../docs/framework/winforms/advanced/media/csfontstext7.png "csfontstext7")</span></span>  
  
 <span data-ttu-id="e4d7c-124">Arial.tff (który został dodany do kolekcji prywatnych czcionki w poniższym przykładzie kodu) jest plikiem czcionki Arial stylu regularne.</span><span class="sxs-lookup"><span data-stu-id="e4d7c-124">Arial.tff (which was added to the private font collection in the following code example) is the font file for the Arial regular style.</span></span> <span data-ttu-id="e4d7c-125">Należy jednak pamiętać, że program dane wyjściowe zawierają dostępne style kilka innych niż zwykła dla rodziny czcionek Arial.</span><span class="sxs-lookup"><span data-stu-id="e4d7c-125">Note, however, that the program output shows several available styles other than regular for the Arial font family.</span></span> <span data-ttu-id="e4d7c-126">Jest to spowodowane tym [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] można symulować pogrubienie, kursywa i bold kursywy od zwykłego stylu.</span><span class="sxs-lookup"><span data-stu-id="e4d7c-126">That is because [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] can simulate the bold, italic, and bold italic styles from the regular style.</span></span> [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]<span data-ttu-id="e4d7c-127">można również utworzyć różne podkreślenia i przekreślenia od zwykłego stylu.</span><span class="sxs-lookup"><span data-stu-id="e4d7c-127"> can also produce underlines and strikeouts from the regular style.</span></span>  
  
 <span data-ttu-id="e4d7c-128">Podobnie [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] można symulować bold styl kursywą z albo bold stylu lub kursywą.</span><span class="sxs-lookup"><span data-stu-id="e4d7c-128">Similarly, [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] can simulate the bold italic style from either the bold style or the italic style.</span></span> <span data-ttu-id="e4d7c-129">Dane wyjściowe programu zawiera styl pogrubiony kursywą jest dostępna dla systemów z rodziny razy, nawet jeśli jest to jedyny TimesBd.tff (razy nowe łacińskich, pogrubione) pliku razy w kolekcji.</span><span class="sxs-lookup"><span data-stu-id="e4d7c-129">The program output shows that the bold italic style is available for the Times family even though TimesBd.tff (Times New Roman, bold) is the only Times file in the collection.</span></span>  
  
 [!code-csharp[System.Drawing.FontsAndText#51](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.FontsAndText/CS/Class1.cs#51)]
 [!code-vb[System.Drawing.FontsAndText#51](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.FontsAndText/VB/Class1.vb#51)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="e4d7c-130">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="e4d7c-130">Compiling the Code</span></span>  
 <span data-ttu-id="e4d7c-131">Powyższy przykład jest przeznaczony do użytku z formularzy systemu Windows i wymaga <xref:System.Windows.Forms.PaintEventArgs> `e`, który jest parametrem <xref:System.Windows.Forms.PaintEventHandler>.</span><span class="sxs-lookup"><span data-stu-id="e4d7c-131">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs> `e`, which is a parameter of <xref:System.Windows.Forms.PaintEventHandler>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e4d7c-132">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e4d7c-132">See Also</span></span>  
 <xref:System.Drawing.Text.PrivateFontCollection>  
 [<span data-ttu-id="e4d7c-133">Używanie czcionek i tekstu</span><span class="sxs-lookup"><span data-stu-id="e4d7c-133">Using Fonts and Text</span></span>](../../../../docs/framework/winforms/advanced/using-fonts-and-text.md)
