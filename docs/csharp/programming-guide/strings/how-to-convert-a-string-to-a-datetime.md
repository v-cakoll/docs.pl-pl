---
title: "Porady: konwertowanie ciągu na DateTime (Przewodnik programowania w języku C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords: strings [C#], converting to DateTIme
ms.assetid: 88abef11-3a06-4b49-8dd2-61ed0e876fc3
caps.latest.revision: "21"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: b459f245f0090fff16918bceb12a0082f6944331
ms.sourcegitcommit: 7e99f66ef09d2903e22c789c67ff5a10aa953b2f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/18/2017
---
# <a name="how-to-convert-a-string-to-a-datetime-c-programming-guide"></a><span data-ttu-id="f1a1b-102">Porady: konwertowanie ciągu na DateTime (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="f1a1b-102">How to: Convert a String to a DateTime (C# Programming Guide)</span></span>
<span data-ttu-id="f1a1b-103">Jest typowe dla programów umożliwić użytkownikom wprowadzanie dat jako wartości parametrów.</span><span class="sxs-lookup"><span data-stu-id="f1a1b-103">It is common for programs to enable users to enter dates as string values.</span></span> <span data-ttu-id="f1a1b-104">Aby przekonwertować datę na podstawie ciągu do <xref:System.DateTime?displayProperty=nameWithType> obiektu, można użyć <xref:System.Convert.ToDateTime%28System.String%29?displayProperty=nameWithType> metody lub <xref:System.DateTime.Parse%28System.String%29?displayProperty=nameWithType> metody statycznej, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="f1a1b-104">To convert a string-based date to a <xref:System.DateTime?displayProperty=nameWithType> object, you can use the <xref:System.Convert.ToDateTime%28System.String%29?displayProperty=nameWithType> method or the <xref:System.DateTime.Parse%28System.String%29?displayProperty=nameWithType> static method, as shown in the following example.</span></span>  
  
 <span data-ttu-id="f1a1b-105">**Kultura**.</span><span class="sxs-lookup"><span data-stu-id="f1a1b-105">**Culture**.</span></span>  <span data-ttu-id="f1a1b-106">Innych kultur na świecie zapisu ciągów daty na różne sposoby.</span><span class="sxs-lookup"><span data-stu-id="f1a1b-106">Different cultures in the world write date strings in different ways.</span></span>  <span data-ttu-id="f1a1b-107">Na przykład w Stanach Zjednoczonych 2008-01-20 jest 20 stycznia 2008.</span><span class="sxs-lookup"><span data-stu-id="f1a1b-107">For example, in the US 01/20/2008 is January 20th, 2008.</span></span>  <span data-ttu-id="f1a1b-108">W Francja zgłosi InvalidFormatException.</span><span class="sxs-lookup"><span data-stu-id="f1a1b-108">In France this will throw an InvalidFormatException.</span></span> <span data-ttu-id="f1a1b-109">To dlatego Francja odczytuje Data razy, ile miesiąc/dzień/rok, a w Stanach Zjednoczonych jest miesiąc/dzień/rok.</span><span class="sxs-lookup"><span data-stu-id="f1a1b-109">This is because France reads date-times as Day/Month/Year, and in the US it is Month/Day/Year.</span></span>  
  
 <span data-ttu-id="f1a1b-110">W rezultacie ciąg tak, 2008-20-01 przeanalizować do 20 stycznia 2008 w Francja, a następnie throw InvalidFormatException w Stanach Zjednoczonych.</span><span class="sxs-lookup"><span data-stu-id="f1a1b-110">Consequently, a string like 20/01/2008 will parse to January 20th, 2008 in France, and then throw an InvalidFormatException in the US.</span></span>  
  
 <span data-ttu-id="f1a1b-111">Aby określić bieżące ustawienia kultury, można użyć System.Globalization.CultureInfo.CurrentCulture.</span><span class="sxs-lookup"><span data-stu-id="f1a1b-111">To determine your current culture settings, you can use System.Globalization.CultureInfo.CurrentCulture.</span></span>  
  
 <span data-ttu-id="f1a1b-112">Zobacz przykład poniżej prosty przykład konwertowanie ciągu na dateTime.</span><span class="sxs-lookup"><span data-stu-id="f1a1b-112">See the example below for a simple example of converting a string to dateTime.</span></span>  
  
 <span data-ttu-id="f1a1b-113">Więcej przykładów ciągów daty, zobacz <xref:System.Convert.ToDateTime%28System.String%29?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="f1a1b-113">For more examples of date strings, see <xref:System.Convert.ToDateTime%28System.String%29?displayProperty=nameWithType>.</span></span>  
  
```csharp  
string dateTime = "01/08/2008 14:50:50.42";  
            DateTime dt = Convert.ToDateTime(dateTime);  
            Console.WriteLine("Year: {0}, Month: {1}, Day: {2}, Hour: {3}, Minute: {4}, Second: {5}, Millisecond: {6}",  
                              dt.Year, dt.Month, dt.Day, dt.Hour, dt.Minute, dt.Second, dt.Millisecond);  
            // Specify exactly how to interpret the string.  
            IFormatProvider culture = new System.Globalization.CultureInfo("fr-FR", true);  
  
            // Alternate choice: If the string has been input by an end user, you might    
            // want to format it according to the current culture:   
            // IFormatProvider culture = System.Threading.Thread.CurrentThread.CurrentCulture;  
            DateTime dt2 = DateTime.Parse(dateTime, culture, System.Globalization.DateTimeStyles.AssumeLocal);  
            Console.WriteLine("Year: {0}, Month: {1}, Day: {2}, Hour: {3}, Minute: {4}, Second: {5}, Millisecond: {6}",  
                              dt2.Year, dt2.Month, dt2.Day, dt2.Hour, dt2.Minute, dt2.Second, dt2.Millisecond  
/* Output (assuming first culture is en-US and second is fr-FR):  
    Year: 2008, Month: 1, Day: 8, Hour: 14, Minute: 50, Second: 50, Millisecond: 420  
Year: 2008, Month: 8, Day: 1, Hour: 14, Minute: 50, Second: 50, Millisecond: 420  
Press any key to continue . . .  
 */  
```  
  
## <a name="example"></a><span data-ttu-id="f1a1b-114">Przykład</span><span class="sxs-lookup"><span data-stu-id="f1a1b-114">Example</span></span>  
 [!code-csharp[csProgGuideStrings#13](../../../csharp/programming-guide/strings/codesnippet/CSharp/how-to-convert-a-string-to-a-datetime_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="f1a1b-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f1a1b-115">See Also</span></span>  
 [<span data-ttu-id="f1a1b-116">Ciągi</span><span class="sxs-lookup"><span data-stu-id="f1a1b-116">Strings</span></span>](../../../csharp/programming-guide/strings/index.md)
