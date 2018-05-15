---
title: Lokalizacja działania
ms.date: 03/30/2017
ms.assetid: 8ee7bc16-e609-469a-a3e8-8062952e2676
ms.openlocfilehash: 23a6d5c2ed202f030397eb70382896468a68a724
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="activity-localization"></a><span data-ttu-id="69299-102">Lokalizacja działania</span><span class="sxs-lookup"><span data-stu-id="69299-102">Activity Localization</span></span>
<span data-ttu-id="69299-103">Jeśli przepływ pracy aplikacji i składników może być zlokalizowana na innych kultur i języków, ciągów zasobów powinien być używany, dzięki czemu może być lokalizowany bez konieczności ponownego kompilowania.</span><span class="sxs-lookup"><span data-stu-id="69299-103">When workflow applications and components have the potential to be localized into other cultures and languages, resource strings should be used so that they can be localized without recompiling.</span></span>  
  
## <a name="activity-localization"></a><span data-ttu-id="69299-104">Lokalizacja działania</span><span class="sxs-lookup"><span data-stu-id="69299-104">Activity Localization</span></span>  
 <span data-ttu-id="69299-105">Jako z wszystkich aplikacji, które muszą być lokalizowany (wydane w różnych wersjach dla różnych języków i kultur), dowolne ciągi, które są wyświetlane użytkownikowi powinien nie można umieścić bezpośrednio w kodzie, ale raczej przechowywane w pliku zasobów.</span><span class="sxs-lookup"><span data-stu-id="69299-105">As with all applications that must be localized (released in different versions for different languages and cultures), any strings that are displayed to the user should not be put directly in code, but rather stored in a resource file.</span></span> <span data-ttu-id="69299-106">Następnie można możliwy ciągi za pośrednictwem <!--zz <xref:System.Environment.GetResourceString> --> `GetResourceString`.</span><span class="sxs-lookup"><span data-stu-id="69299-106">The strings can then be accessed through <!--zz <xref:System.Environment.GetResourceString> --> `GetResourceString`.</span></span> <span data-ttu-id="69299-107">Jeśli tworzysz składnik, który jest dystrybuowane w różnych językach, należy użyć ciągów zasobów dla komunikatów dotyczących sprawdzania poprawności działania, zdefiniowane przez użytkownika śledzenia danych, komunikaty śledzenia i komunikaty o błędach oraz.</span><span class="sxs-lookup"><span data-stu-id="69299-107">If you are developing a component that is distributed in several languages, you also want to use resource strings for activity validation messages, user-defined tracking data, tracing messages, and error messages as well.</span></span>  
  
 <span data-ttu-id="69299-108">Poniższym ćwiczeniu przedstawiono sposób użycia pliku zasobu.</span><span class="sxs-lookup"><span data-stu-id="69299-108">The following exercise demonstrates how to use a resource file.</span></span>  
  
#### <a name="using-resource-files-for-localized-strings"></a><span data-ttu-id="69299-109">Przy użyciu plików zasobów dla zlokalizowanych ciągów</span><span class="sxs-lookup"><span data-stu-id="69299-109">Using resource files for localized strings</span></span>  
  
1.  <span data-ttu-id="69299-110">W [!INCLUDE[vs2010](../../../includes/vs2010-md.md)], kliknij prawym przyciskiem myszy projekt w **Eksploratora rozwiązań** i wybierz **Dodaj...** , **Nowy element...** .</span><span class="sxs-lookup"><span data-stu-id="69299-110">In [!INCLUDE[vs2010](../../../includes/vs2010-md.md)], right-click your project in **Solution Explorer** and select **Add…**, **New Item…**.</span></span>  
  
2.  <span data-ttu-id="69299-111">Wybierz **pliku zasobów** i nazwij plik ErrorResources.resx.</span><span class="sxs-lookup"><span data-stu-id="69299-111">Select **Resources File** and name the file ErrorResources.resx.</span></span> <span data-ttu-id="69299-112">Kliknij przycisk **Dodaj**.</span><span class="sxs-lookup"><span data-stu-id="69299-112">Click **Add**.</span></span>  
  
3.  <span data-ttu-id="69299-113">Otwórz plik zasobu.</span><span class="sxs-lookup"><span data-stu-id="69299-113">Open the resource file.</span></span> <span data-ttu-id="69299-114">Dodaj nowy wpis o **nazwa** z ErrorString i **wartość** "działania nie jest prawidłowy."</span><span class="sxs-lookup"><span data-stu-id="69299-114">Add a new entry with a **Name** of ErrorString and a **Value** of "The activity is not valid."</span></span>  
  
4.  <span data-ttu-id="69299-115">Dodaj następujące `using` instrukcje do swojej klasy.</span><span class="sxs-lookup"><span data-stu-id="69299-115">Add the following `using` statements to your class.</span></span>  
  
    ```  
    using System.Reflection;  
    using System.Resources;  
    ```  
  
5.  <span data-ttu-id="69299-116">Utwórz zasób menedżera w projekcie.</span><span class="sxs-lookup"><span data-stu-id="69299-116">Create a resource manager in your project.</span></span>  
  
    ```  
    ResourceManager ErrorManager;  
    ...  
    ErrorManager = new ResourceManager("MyNamespace.ErrorResources", Assembly.GetExecutingAssembly());  
    ```  
  
6.  <span data-ttu-id="69299-117">Pobrać ciąg Menedżera zasobów, w których jest wymagane.</span><span class="sxs-lookup"><span data-stu-id="69299-117">Get the string from the resource manager where it is required.</span></span>  
  
    ```  
    String errorMessage = ErrorManager.GetString("ErrorString");  
    ```  
  
 <span data-ttu-id="69299-118">Poniższy przykład kodu pokazuje, jak korzystać z zlokalizowanych ciągów w <xref:System.Activities.Activity.CacheMetadata%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="69299-118">The following code sample demonstrates how to utilize localized strings in the <xref:System.Activities.Activity.CacheMetadata%2A> method.</span></span>  
  
```  
       protected override void CacheMetadata(CodeActivityMetadata metadata)  
        {  
           .....  
          // rest of the code elided for brevity  
           .....  
            if (this.Value != null && this.To != null)  
            {  
                if (!TypeHelper.AreTypesCompatible(this.Value.ArgumentType, this.To.ArgumentType))  
                {  
//---------------------------------------------  
// ** SR.TypeMismatchForAssign will fetch the string from the resource manager **  
//---------------------------------------------  
                    metadata.AddValidationError(SR.TypeMismatchForAssign(  
                                this.Value.ArgumentType,  
                                this.To.ArgumentType,  
                                this.DisplayName));  
                }  
            }  
        }  
```
