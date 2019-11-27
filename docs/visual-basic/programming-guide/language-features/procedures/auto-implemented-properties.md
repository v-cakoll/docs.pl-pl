---
title: Właściwości zaimplementowane automatycznie
ms.date: 07/20/2015
f1_keywords:
- vb.AutoProperty
- vb.AutoImplementedProperty
helpviewer_keywords:
- properties [Visual Basic], auto-implemented
- auto-implemented properties [Visual Basic]
ms.assetid: 5c669f0b-cf95-4b4e-ae84-9cc55212ca87
ms.openlocfilehash: b322bd2215c95298be0a33ace1f3590a63878e24
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74350383"
---
# <a name="auto-implemented-properties-visual-basic"></a><span data-ttu-id="8c565-102">Właściwości zaimplementowane automatycznie (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8c565-102">Auto-Implemented Properties (Visual Basic)</span></span>
<span data-ttu-id="8c565-103">*Zaimplementowane właściwości* umożliwiają szybkie określenie właściwości klasy bez konieczności pisania kodu do `Get` i `Set` właściwości.</span><span class="sxs-lookup"><span data-stu-id="8c565-103">*Auto-implemented properties* enable you to quickly specify a property of a class without having to write code to `Get` and `Set` the property.</span></span> <span data-ttu-id="8c565-104">Podczas pisania kodu dla właściwości automatycznej implementacji kompilator Visual Basic automatycznie tworzy pole prywatne do przechowywania zmiennej właściwości oprócz tworzenia skojarzonych `Get` i `Set` procedur.</span><span class="sxs-lookup"><span data-stu-id="8c565-104">When you write code for an auto-implemented property, the Visual Basic compiler automatically creates a private field to store the property variable in addition to creating the associated `Get` and `Set` procedures.</span></span>  
  
 <span data-ttu-id="8c565-105">Przy użyciu właściwości, które są implementowane przez program, właściwość, w tym wartość domyślną, może być zadeklarowana w jednym wierszu.</span><span class="sxs-lookup"><span data-stu-id="8c565-105">With auto-implemented properties, a property, including a default value, can be declared in a single line.</span></span> <span data-ttu-id="8c565-106">Poniższy przykład przedstawia trzy deklaracje właściwości.</span><span class="sxs-lookup"><span data-stu-id="8c565-106">The following example shows three property declarations.</span></span>  
  
 [!code-vb[VbVbalrAutoImplementedProperties#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrautoimplementedproperties/vb/module1.vb#1)]  
  
 <span data-ttu-id="8c565-107">Właściwość zaimplementowana przez funkcję jest równoważna właściwości, dla której wartość właściwości jest przechowywana w polu prywatnym.</span><span class="sxs-lookup"><span data-stu-id="8c565-107">An auto-implemented property is equivalent to a property for which the property value is stored in a private field.</span></span> <span data-ttu-id="8c565-108">Poniższy przykład kodu pokazuje właściwość, która jest implementowana.</span><span class="sxs-lookup"><span data-stu-id="8c565-108">The following code example shows an auto-implemented property.</span></span>  
  
 [!code-vb[VbVbalrAutoImplementedProperties#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrautoimplementedproperties/vb/module1.vb#5)]  
  
 <span data-ttu-id="8c565-109">Poniższy przykład kodu pokazuje odpowiedni kod dla poprzedniego przykładu zaimplementowanej właściwości.</span><span class="sxs-lookup"><span data-stu-id="8c565-109">The following code example shows the equivalent code for the previous auto-implemented property example.</span></span>  
  
 [!code-vb[VbVbalrAutoImplementedProperties#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrautoimplementedproperties/vb/module1.vb#2)]  
  
 <span data-ttu-id="8c565-110">Poniższy kod przedstawia implementowanie właściwości ReadOnly:</span><span class="sxs-lookup"><span data-stu-id="8c565-110">The following code show implementing readonly properties:</span></span>  
  
```vb  
Class Customer  
   Public ReadOnly Property Tags As New List(Of String)  
   Public ReadOnly Property Name As String = ""  
   Public ReadOnly Property File As String  
  
   Sub New(file As String)  
      Me.File = file  
   End Sub  
End Class  
```  
  
 <span data-ttu-id="8c565-111">Można przypisać do właściwości z wyrażeniami inicjalizacji, jak pokazano w przykładzie, lub można przypisać do właściwości w konstruktorze typu zawierającego.</span><span class="sxs-lookup"><span data-stu-id="8c565-111">You can assign to the property with initialization expressions as shown in the example, or you can assign to the properties in the containing type’s constructor.</span></span>  <span data-ttu-id="8c565-112">Można przypisać do pól zapasowych właściwości tylko do odczytu w dowolnym momencie.</span><span class="sxs-lookup"><span data-stu-id="8c565-112">You can assign to the backing fields of readonly properties at any time.</span></span>  
  
## <a name="backing-field"></a><span data-ttu-id="8c565-113">Pole zapasowe</span><span class="sxs-lookup"><span data-stu-id="8c565-113">Backing Field</span></span>  
 <span data-ttu-id="8c565-114">W przypadku deklarowania automatycznie zaimplementowanej właściwości Visual Basic automatycznie tworzy ukryte pole prywatne o nazwie *pole zapasowe* , aby zawierało wartość właściwości.</span><span class="sxs-lookup"><span data-stu-id="8c565-114">When you declare an auto-implemented property, Visual Basic automatically creates a hidden private field called the *backing field* to contain the property value.</span></span> <span data-ttu-id="8c565-115">Nazwa pola zapasowego jest zaimplementowaną nazwą właściwości, poprzedzoną znakiem podkreślenia (_).</span><span class="sxs-lookup"><span data-stu-id="8c565-115">The backing field name is the auto-implemented property name preceded by an underscore (_).</span></span> <span data-ttu-id="8c565-116">Na przykład jeśli zadeklarujesz Właściwość zaimplementowaną przez funkcję `ID`, pole zapasowe ma nazwę `_ID`.</span><span class="sxs-lookup"><span data-stu-id="8c565-116">For example, if you declare an auto-implemented property named `ID`, the backing field is named `_ID`.</span></span> <span data-ttu-id="8c565-117">Jeśli dołączysz element członkowski klasy o nazwie `_ID`, zostanie wygenerowane konflikt nazw i Visual Basic raporty błąd kompilatora.</span><span class="sxs-lookup"><span data-stu-id="8c565-117">If you include a member of your class that is also named `_ID`, you produce a naming conflict and Visual Basic reports a compiler error.</span></span>  
  
 <span data-ttu-id="8c565-118">Pole zapasowe ma również następujące cechy:</span><span class="sxs-lookup"><span data-stu-id="8c565-118">The backing field also has the following characteristics:</span></span>  
  
- <span data-ttu-id="8c565-119">Modyfikator dostępu dla pola zapasowego jest zawsze `Private`, nawet jeśli sama właściwość ma inny poziom dostępu, na przykład `Public`.</span><span class="sxs-lookup"><span data-stu-id="8c565-119">The access modifier for the backing field is always `Private`, even when the property itself has a different access level, such as `Public`.</span></span>  
  
- <span data-ttu-id="8c565-120">Jeśli właściwość jest oznaczona jako `Shared`, pole zapasowe jest również udostępniane.</span><span class="sxs-lookup"><span data-stu-id="8c565-120">If the property is marked as `Shared`, the backing field also is shared.</span></span>  
  
- <span data-ttu-id="8c565-121">Atrybuty określone dla właściwości nie mają zastosowania do pola zapasowego.</span><span class="sxs-lookup"><span data-stu-id="8c565-121">Attributes specified for the property do not apply to the backing field.</span></span>  
  
- <span data-ttu-id="8c565-122">Do pola zapasowego można uzyskać dostęp z kodu w klasie oraz z narzędzi debugowania, takich jak okno wyrażeń kontrolnych.</span><span class="sxs-lookup"><span data-stu-id="8c565-122">The backing field can be accessed from code within the class and from debugging tools such as the Watch window.</span></span> <span data-ttu-id="8c565-123">Jednak pole zapasowe nie jest wyświetlane na liście uzupełniania słów IntelliSense.</span><span class="sxs-lookup"><span data-stu-id="8c565-123">However, the backing field does not show in an IntelliSense word completion list.</span></span>  
  
## <a name="initializing-an-auto-implemented-property"></a><span data-ttu-id="8c565-124">Inicjowanie właściwości, która została zaimplementowana</span><span class="sxs-lookup"><span data-stu-id="8c565-124">Initializing an Auto-Implemented Property</span></span>  
 <span data-ttu-id="8c565-125">Dowolne wyrażenie, które może zostać użyte do zainicjowania pola jest prawidłowe dla inicjowania właściwości, która jest implementowana.</span><span class="sxs-lookup"><span data-stu-id="8c565-125">Any expression that can be used to initialize a field is valid for initializing an auto-implemented property.</span></span> <span data-ttu-id="8c565-126">Po zainicjowaniu właściwości, wyrażenie jest oceniane i przesyłane do `Set` procedury dla właściwości.</span><span class="sxs-lookup"><span data-stu-id="8c565-126">When you initialize an auto-implemented property, the expression is evaluated and passed to the `Set` procedure for the property.</span></span> <span data-ttu-id="8c565-127">W poniższych przykładach kodu przedstawiono niektóre zaimplementowane właściwości, które zawierają wartości początkowe.</span><span class="sxs-lookup"><span data-stu-id="8c565-127">The following code examples show some auto-implemented properties that include initial values.</span></span>  
  
 [!code-vb[VbVbalrAutoImplementedProperties#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrautoimplementedproperties/vb/module1.vb#3)]  
  
 <span data-ttu-id="8c565-128">Nie można zainicjować właściwości, która jest zaimplementowana, która jest elementem członkowskim `Interface`lub którą oznaczono `MustOverride`.</span><span class="sxs-lookup"><span data-stu-id="8c565-128">You cannot initialize an auto-implemented property that is a member of an `Interface`, or one that is marked `MustOverride`.</span></span>  
  
 <span data-ttu-id="8c565-129">W przypadku deklarowania właściwości, która jest implementowana jako element członkowski `Structure`, można zainicjować tylko Właściwość zaimplementowaną, jeśli jest ona oznaczona jako `Shared`.</span><span class="sxs-lookup"><span data-stu-id="8c565-129">When you declare an auto-implemented property as a member of a `Structure`, you can only initialize the auto-implemented property if it is marked as `Shared`.</span></span>  
  
 <span data-ttu-id="8c565-130">W przypadku deklarowania właściwości, która jest zaimplementowana jako tablica, nie można określić jawnych granic tablicy.</span><span class="sxs-lookup"><span data-stu-id="8c565-130">When you declare an auto-implemented property as an array, you cannot specify explicit array bounds.</span></span> <span data-ttu-id="8c565-131">Można jednak podać wartość przy użyciu inicjatora tablicy, jak pokazano w poniższych przykładach.</span><span class="sxs-lookup"><span data-stu-id="8c565-131">However, you can supply a value by using an array initializer, as shown in the following examples.</span></span>  
  
 [!code-vb[VbVbalrAutoImplementedProperties#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrautoimplementedproperties/vb/module1.vb#4)]  
  
## <a name="property-definitions-that-require-standard-syntax"></a><span data-ttu-id="8c565-132">Definicje właściwości, które wymagają standardowej składni</span><span class="sxs-lookup"><span data-stu-id="8c565-132">Property Definitions That Require Standard Syntax</span></span>  
 <span data-ttu-id="8c565-133">Właściwości zaimplementowane przez funkcję są wygodne i obsługują wiele scenariuszy programowania.</span><span class="sxs-lookup"><span data-stu-id="8c565-133">Auto-implemented properties are convenient and support many programming scenarios.</span></span> <span data-ttu-id="8c565-134">Istnieją jednak sytuacje, w których nie można użyć właściwości, która jest zaimplementowana, a zamiast tego należy użyć standardowej lub *rozwiniętej*składni właściwości.</span><span class="sxs-lookup"><span data-stu-id="8c565-134">However, there are situations in which you cannot use an auto-implemented property and must instead use standard, or *expanded*, property syntax.</span></span>  
  
 <span data-ttu-id="8c565-135">Musisz użyć rozwiniętej składni definicji właściwości, jeśli chcesz wykonać jedną z następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="8c565-135">You have to use expanded property-definition syntax if you want to do any one of the following:</span></span>  
  
- <span data-ttu-id="8c565-136">Dodaj kod do procedury `Get` lub `Set` właściwości, takiej jak kod, aby zweryfikować wartości przychodzące w procedurze `Set`.</span><span class="sxs-lookup"><span data-stu-id="8c565-136">Add code to the `Get` or `Set` procedure of a property, such as code to validate incoming values in the `Set` procedure.</span></span> <span data-ttu-id="8c565-137">Na przykład możesz chcieć sprawdzić, czy ciąg reprezentujący numer telefonu zawiera wymaganą liczbę cyfr przed ustawieniem wartości właściwości.</span><span class="sxs-lookup"><span data-stu-id="8c565-137">For example, you might want to verify that a string that represents a telephone number contains the required number of numerals before setting the property value.</span></span>  
  
- <span data-ttu-id="8c565-138">Określ różne ułatwienia dostępu dla procedury `Get` i `Set`.</span><span class="sxs-lookup"><span data-stu-id="8c565-138">Specify different accessibility for the `Get` and `Set` procedure.</span></span> <span data-ttu-id="8c565-139">Na przykład możesz chcieć wykonać `Set` procedury `Private` i `Get` procedurę `Public`.</span><span class="sxs-lookup"><span data-stu-id="8c565-139">For example, you might want to make the `Set` procedure `Private` and the `Get` procedure `Public`.</span></span>  
  
- <span data-ttu-id="8c565-140">Utwórz właściwości, które są `WriteOnly`.</span><span class="sxs-lookup"><span data-stu-id="8c565-140">Create properties that are `WriteOnly`.</span></span>  
  
- <span data-ttu-id="8c565-141">Użyj właściwości sparametryzowanych (w tym `Default` właściwości).</span><span class="sxs-lookup"><span data-stu-id="8c565-141">Use parameterized properties (including `Default` properties).</span></span> <span data-ttu-id="8c565-142">Należy zadeklarować rozwiniętą właściwość w celu określenia parametru właściwości lub określić dodatkowe parametry procedury `Set`.</span><span class="sxs-lookup"><span data-stu-id="8c565-142">You must declare an expanded property in order to specify a parameter for the property, or to specify additional parameters for the `Set` procedure.</span></span>  
  
- <span data-ttu-id="8c565-143">Umieść atrybut w polu zapasowym lub zmień poziom dostępu pola zapasowego.</span><span class="sxs-lookup"><span data-stu-id="8c565-143">Place an attribute on the backing field, or change the access level of the backing field.</span></span>  
  
- <span data-ttu-id="8c565-144">Podaj Komentarze XML dla pola zapasowego.</span><span class="sxs-lookup"><span data-stu-id="8c565-144">Provide XML comments for the backing field.</span></span>  
  
## <a name="expanding-an-auto-implemented-property"></a><span data-ttu-id="8c565-145">Rozwijanie właściwości, która jest implementowana</span><span class="sxs-lookup"><span data-stu-id="8c565-145">Expanding an Auto-Implemented Property</span></span>  
 <span data-ttu-id="8c565-146">Jeśli konieczne jest przekonwertowanie automatycznie zaimplementowanej właściwości na rozwiniętą właściwość, która zawiera procedurę `Get` lub `Set`, Edytor kodu Visual Basic może automatycznie generować procedury `Get` i `Set` oraz `End Property` instrukcję dla właściwości.</span><span class="sxs-lookup"><span data-stu-id="8c565-146">If you have to convert an auto-implemented property to an expanded property that contains a `Get` or `Set` procedure, the Visual Basic Code Editor can automatically generate the `Get` and `Set` procedures and `End Property` statement for the property.</span></span> <span data-ttu-id="8c565-147">Kod jest generowany, gdy umieścisz kursor w pustym wierszu po instrukcji `Property`, wpisz `G` (dla `Get`) lub `S` (dla `Set`) i naciśnij klawisz ENTER.</span><span class="sxs-lookup"><span data-stu-id="8c565-147">The code is generated if you put the cursor on a blank line following the `Property` statement, type a `G` (for `Get`) or an `S` (for `Set`) and press ENTER.</span></span> <span data-ttu-id="8c565-148">Visual Basic Edytor kodu automatycznie generuje procedurę `Get` lub `Set` dla właściwości tylko do odczytu i tylko do zapisu po naciśnięciu klawisza ENTER na końcu instrukcji `Property`.</span><span class="sxs-lookup"><span data-stu-id="8c565-148">The Visual Basic Code Editor automatically generates the `Get` or `Set` procedure for read-only and write-only properties when you press ENTER at the end of a `Property` statement.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8c565-149">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8c565-149">See also</span></span>

- [<span data-ttu-id="8c565-150">Instrukcje: deklarowanie i wywoływanie właściwości domyślnej w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="8c565-150">How to: Declare and Call a Default Property in Visual Basic</span></span>](./how-to-declare-and-call-a-default-property.md)
- [<span data-ttu-id="8c565-151">Instrukcje: deklarowanie właściwości z mieszanymi poziomami dostępu</span><span class="sxs-lookup"><span data-stu-id="8c565-151">How to: Declare a Property with Mixed Access Levels</span></span>](./how-to-declare-a-property-with-mixed-access-levels.md)
- [<span data-ttu-id="8c565-152">Property, instrukcja</span><span class="sxs-lookup"><span data-stu-id="8c565-152">Property Statement</span></span>](../../../../visual-basic/language-reference/statements/property-statement.md)
- [<span data-ttu-id="8c565-153">ReadOnly</span><span class="sxs-lookup"><span data-stu-id="8c565-153">ReadOnly</span></span>](../../../../visual-basic/language-reference/modifiers/readonly.md)
- [<span data-ttu-id="8c565-154">WriteOnly</span><span class="sxs-lookup"><span data-stu-id="8c565-154">WriteOnly</span></span>](../../../../visual-basic/language-reference/modifiers/writeonly.md)
- [<span data-ttu-id="8c565-155">Obiekty i klasy</span><span class="sxs-lookup"><span data-stu-id="8c565-155">Objects and Classes</span></span>](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
