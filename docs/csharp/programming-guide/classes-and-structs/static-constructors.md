---
title: Konstruktory statyczne (Przewodnik programowania w języku C#)
ms.date: 07/20/2015
helpviewer_keywords:
- static constructors [C#]
- constructors [C#], static
ms.assetid: 151ec95e-3c4d-4ed7-885d-95b7a3be2e7d
ms.openlocfilehash: 22be72547e96c66df3be115dac30a16559b23659
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43502771"
---
# <a name="static-constructors-c-programming-guide"></a><span data-ttu-id="ad895-102">Konstruktory statyczne (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="ad895-102">Static Constructors (C# Programming Guide)</span></span>
<span data-ttu-id="ad895-103">Statyczny Konstruktor jest wykorzystywany do inicjacji dowolne [statyczne](../../../csharp/language-reference/keywords/static.md) danych, lub do wykonania określonej akcji, która musi zostać wykonana tylko raz.</span><span class="sxs-lookup"><span data-stu-id="ad895-103">A static constructor is used to initialize any [static](../../../csharp/language-reference/keywords/static.md) data, or to perform a particular action that needs to be performed once only.</span></span> <span data-ttu-id="ad895-104">Jest wywoływana automatycznie przed pierwsze wystąpienie jest tworzone lub żadnych statycznych składowych są wywoływane.</span><span class="sxs-lookup"><span data-stu-id="ad895-104">It is called automatically before the first instance is created or any static members are referenced.</span></span>  
  
 [!code-csharp[csProgGuideObjects#14](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/static-constructors_1.cs)]  
  
 <span data-ttu-id="ad895-105">Konstruktory statyczne mają następujące właściwości:</span><span class="sxs-lookup"><span data-stu-id="ad895-105">Static constructors have the following properties:</span></span>  
  
-   <span data-ttu-id="ad895-106">Statyczny Konstruktor zająć modyfikatory dostępu lub nie mieć parametrów.</span><span class="sxs-lookup"><span data-stu-id="ad895-106">A static constructor does not take access modifiers or have parameters.</span></span>  
  
-   <span data-ttu-id="ad895-107">Statyczny Konstruktor jest wywoływana automatycznie zainicjować [klasy](../../../csharp/language-reference/keywords/class.md) przed pierwsze wystąpienie jest tworzone lub żadnych statycznych składowych są wywoływane.</span><span class="sxs-lookup"><span data-stu-id="ad895-107">A static constructor is called automatically to initialize the [class](../../../csharp/language-reference/keywords/class.md) before the first instance is created or any static members are referenced.</span></span>  
  
-   <span data-ttu-id="ad895-108">Konstruktor statyczny nie może wywołać bezpośrednio.</span><span class="sxs-lookup"><span data-stu-id="ad895-108">A static constructor cannot be called directly.</span></span>  
  
-   <span data-ttu-id="ad895-109">Użytkownik nie ma kontroli na gdy Konstruktor statyczny jest wykonywane w programie.</span><span class="sxs-lookup"><span data-stu-id="ad895-109">The user has no control on when the static constructor is executed in the program.</span></span>  
  
-   <span data-ttu-id="ad895-110">Typowym zastosowaniem konstruktorów statycznych jest, gdy klasa korzysta z pliku dziennika i konstruktora jest używany do zapisywania wpisów w tym pliku.</span><span class="sxs-lookup"><span data-stu-id="ad895-110">A typical use of static constructors is when the class is using a log file and the constructor is used to write entries to this file.</span></span>  
  
-   <span data-ttu-id="ad895-111">Konstruktory statyczne są także przydatne przy tworzeniu klas otoki dla niezarządzanego kodu podczas można wywołać konstruktora `LoadLibrary` metody.</span><span class="sxs-lookup"><span data-stu-id="ad895-111">Static constructors are also useful when creating wrapper classes for unmanaged code, when the constructor can call the `LoadLibrary` method.</span></span>  
  
-   <span data-ttu-id="ad895-112">Jeśli statyczny Konstruktor zgłasza wyjątek, środowisko wykonawcze nie wywoła go drugi raz, a typ pozostanie niezainicjowanej okres istnienia domeny aplikacji, w którym jest uruchomiony program.</span><span class="sxs-lookup"><span data-stu-id="ad895-112">If a static constructor throws an exception, the runtime will not invoke it a second time, and the type will remain uninitialized for the lifetime of the application domain in which your program is running.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ad895-113">Przykład</span><span class="sxs-lookup"><span data-stu-id="ad895-113">Example</span></span>  
 <span data-ttu-id="ad895-114">W tym przykładzie klasa `Bus` ma Konstruktor statyczny.</span><span class="sxs-lookup"><span data-stu-id="ad895-114">In this example, class `Bus` has a static constructor.</span></span> <span data-ttu-id="ad895-115">Po pierwsze wystąpienie `Bus` zostanie utworzony (`bus1`), statyczny Konstruktor jest wywoływane w celu zainicjowania klasy.</span><span class="sxs-lookup"><span data-stu-id="ad895-115">When the first instance of `Bus` is created (`bus1`), the static constructor is invoked to initialize the class.</span></span> <span data-ttu-id="ad895-116">Przykładowe dane wyjściowe weryfikuje, że Konstruktor statyczny działa tylko jeden raz, nawet jeśli dwa wystąpienia `Bus` są tworzone, to jest uruchamiane przed uruchomieniem konstruktora wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="ad895-116">The sample output verifies that the static constructor runs only one time, even though two instances of `Bus` are created, and that it runs before the instance constructor runs.</span></span>  
  
 [!code-csharp[csProgGuideObjects#15](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/static-constructors_2.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="ad895-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ad895-117">See Also</span></span>

- [<span data-ttu-id="ad895-118">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="ad895-118">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="ad895-119">Klasy i struktury</span><span class="sxs-lookup"><span data-stu-id="ad895-119">Classes and Structs</span></span>](../../../csharp/programming-guide/classes-and-structs/index.md)  
- [<span data-ttu-id="ad895-120">Konstruktory</span><span class="sxs-lookup"><span data-stu-id="ad895-120">Constructors</span></span>](../../../csharp/programming-guide/classes-and-structs/constructors.md)  
- [<span data-ttu-id="ad895-121">Klasy statyczne i statyczne elementy członkowskie klas</span><span class="sxs-lookup"><span data-stu-id="ad895-121">Static Classes and Static Class Members</span></span>](../../../csharp/programming-guide/classes-and-structs/static-classes-and-static-class-members.md)  
- [<span data-ttu-id="ad895-122">Finalizatory</span><span class="sxs-lookup"><span data-stu-id="ad895-122">Finalizers</span></span>](../../../csharp/programming-guide/classes-and-structs/destructors.md)
