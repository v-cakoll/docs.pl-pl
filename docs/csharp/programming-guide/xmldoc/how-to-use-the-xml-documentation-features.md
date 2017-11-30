---
title: "Porady: użycie funkcji dokumentacji XML (Przewodnik programowania w języku C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- XML documentation [C#]
- C# language, XML documentation features
ms.assetid: 8f33917b-9577-4c9a-818a-640dbbb0b399
caps.latest.revision: "19"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: eb647a275a5cd5fac2316706591440d9792861b3
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-use-the-xml-documentation-features-c-programming-guide"></a><span data-ttu-id="cda6e-102">Porady: użycie funkcji dokumentacji XML (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="cda6e-102">How to: Use the XML Documentation Features (C# Programming Guide)</span></span>
<span data-ttu-id="cda6e-103">Poniższy przykład zawiera ogólne omówienie typu, który został udokumentowany.</span><span class="sxs-lookup"><span data-stu-id="cda6e-103">The following sample provides a basic overview of a type that has been documented.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cda6e-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="cda6e-104">Example</span></span>  
 [!code-csharp[csProgGuideDocComments#15](../../../csharp/programming-guide/xmldoc/codesnippet/CSharp/how-to-use-the-xml-documentation-features_1.cs)]  
  
 <span data-ttu-id="cda6e-105">**Ten plik XML został wygenerowany z powyższego przykładu kodu.**</span><span class="sxs-lookup"><span data-stu-id="cda6e-105">**// This .xml file was generated with the previous code sample.**</span></span>  
<span data-ttu-id="cda6e-106">**\<? wersji xml = "1.0"? >**</span><span class="sxs-lookup"><span data-stu-id="cda6e-106">**\<?xml version="1.0"?>**</span></span>  
<span data-ttu-id="cda6e-107">**\<doc >**</span><span class="sxs-lookup"><span data-stu-id="cda6e-107">**\<doc>**</span></span>  
 <span data-ttu-id="cda6e-108">**\<zestaw >**</span><span class="sxs-lookup"><span data-stu-id="cda6e-108">**\<assembly>**</span></span>  
 <span data-ttu-id="cda6e-109">**\<nazwa > xmlsample \< /name >**</span><span class="sxs-lookup"><span data-stu-id="cda6e-109">**\<name>xmlsample\</name>**</span></span>  
 <span data-ttu-id="cda6e-110">**\</ Assembly >**</span><span class="sxs-lookup"><span data-stu-id="cda6e-110">**\</assembly>**</span></span>  
 <span data-ttu-id="cda6e-111">**\<elementy członkowskie >**</span><span class="sxs-lookup"><span data-stu-id="cda6e-111">**\<members>**</span></span>  
 <span data-ttu-id="cda6e-112">**\<Nazwa elementu = "T:SomeClass" >**</span><span class="sxs-lookup"><span data-stu-id="cda6e-112">**\<member name="T:SomeClass">**</span></span>  
 <span data-ttu-id="cda6e-113">**\<podsumowania >**</span><span class="sxs-lookup"><span data-stu-id="cda6e-113">**\<summary>**</span></span>  
 <span data-ttu-id="cda6e-114">**Tutaj należy wstawić poziomu dokumentacji podsumowania klasy.  \< /summary >**</span><span class="sxs-lookup"><span data-stu-id="cda6e-114">**Class level summary documentation goes here.\</summary>**</span></span>  
 <span data-ttu-id="cda6e-115">**\<Remarks >**</span><span class="sxs-lookup"><span data-stu-id="cda6e-115">**\<remarks>**</span></span>  
 <span data-ttu-id="cda6e-116">**Komentarze dłużej może być skojarzony z typu lub elementu członkowskiego**</span><span class="sxs-lookup"><span data-stu-id="cda6e-116">**Longer comments can be associated with a type or member**</span></span>  
 <span data-ttu-id="cda6e-117">**za pomocą tagu uwagi \< /remarks >**</span><span class="sxs-lookup"><span data-stu-id="cda6e-117">**through the remarks tag\</remarks>**</span></span>  
 <span data-ttu-id="cda6e-118">**\</Member >**</span><span class="sxs-lookup"><span data-stu-id="cda6e-118">**\</member>**</span></span>  
 <span data-ttu-id="cda6e-119">**\<element członkowski name="F:SomeClass.m_Name" >**</span><span class="sxs-lookup"><span data-stu-id="cda6e-119">**\<member name="F:SomeClass.m_Name">**</span></span>  
 <span data-ttu-id="cda6e-120">**\<podsumowania >**</span><span class="sxs-lookup"><span data-stu-id="cda6e-120">**\<summary>**</span></span>  
 <span data-ttu-id="cda6e-121">**Magazyn dla właściwości nazwy \< /summary >**</span><span class="sxs-lookup"><span data-stu-id="cda6e-121">**Store for the name property\</summary>**</span></span>  
 <span data-ttu-id="cda6e-122">**\</Member >**</span><span class="sxs-lookup"><span data-stu-id="cda6e-122">**\</member>**</span></span>  
 <span data-ttu-id="cda6e-123">**\<Nazwa elementu = "M:SomeClass. #ctor" >**</span><span class="sxs-lookup"><span data-stu-id="cda6e-123">**\<member name="M:SomeClass.#ctor">**</span></span>  
 <span data-ttu-id="cda6e-124">**\<Podsumowanie > konstruktora klasy.  \< /summary >**</span><span class="sxs-lookup"><span data-stu-id="cda6e-124">**\<summary>The class constructor.\</summary>**</span></span>  
 <span data-ttu-id="cda6e-125">**\</Member >**</span><span class="sxs-lookup"><span data-stu-id="cda6e-125">**\</member>**</span></span>  
 <span data-ttu-id="cda6e-126">**\<element członkowski name="M:SomeClass.SomeMethod(System.String)" >**</span><span class="sxs-lookup"><span data-stu-id="cda6e-126">**\<member name="M:SomeClass.SomeMethod(System.String)">**</span></span>  
 <span data-ttu-id="cda6e-127">**\<podsumowania >**</span><span class="sxs-lookup"><span data-stu-id="cda6e-127">**\<summary>**</span></span>  
 <span data-ttu-id="cda6e-128">**Opis SomeMethod.  \< /summary >**</span><span class="sxs-lookup"><span data-stu-id="cda6e-128">**Description for SomeMethod.\</summary>**</span></span>  
 <span data-ttu-id="cda6e-129">**\<param name = "s" > tutaj opis parametru s\</param >**</span><span class="sxs-lookup"><span data-stu-id="cda6e-129">**\<param name="s"> Parameter description for s goes here\</param>**</span></span>  
 <span data-ttu-id="cda6e-130">**\<SeeAlso cref="T:System.String" >**</span><span class="sxs-lookup"><span data-stu-id="cda6e-130">**\<seealso cref="T:System.String">**</span></span>  
 <span data-ttu-id="cda6e-131">**Atrybut cref dowolny znacznik służy do odwołania, typu lub elementu członkowskiego**</span><span class="sxs-lookup"><span data-stu-id="cda6e-131">**You can use the cref attribute on any tag to reference a type or member**</span></span>  
 <span data-ttu-id="cda6e-132">**i kompilator będzie sprawdzać, czy istnieje odwołanie. \</seealso >**</span><span class="sxs-lookup"><span data-stu-id="cda6e-132">**and the compiler will check that the reference exists. \</seealso>**</span></span>  
 <span data-ttu-id="cda6e-133">**\</Member >**</span><span class="sxs-lookup"><span data-stu-id="cda6e-133">**\</member>**</span></span>  
 <span data-ttu-id="cda6e-134">**\<element członkowski name="M:SomeClass.SomeOtherMethod" >**</span><span class="sxs-lookup"><span data-stu-id="cda6e-134">**\<member name="M:SomeClass.SomeOtherMethod">**</span></span>  
 <span data-ttu-id="cda6e-135">**\<podsumowania >**</span><span class="sxs-lookup"><span data-stu-id="cda6e-135">**\<summary>**</span></span>  
 <span data-ttu-id="cda6e-136">**Innej metody.  \< /summary >**</span><span class="sxs-lookup"><span data-stu-id="cda6e-136">**Some other method. \</summary>**</span></span>  
 <span data-ttu-id="cda6e-137">**\<Zwraca >**</span><span class="sxs-lookup"><span data-stu-id="cda6e-137">**\<returns>**</span></span>  
 <span data-ttu-id="cda6e-138">**Za pomocą tagu zwraca opisano zwracanych wyników.  \< /returns >**</span><span class="sxs-lookup"><span data-stu-id="cda6e-138">**Return results are described through the returns tag.\</returns>**</span></span>  
 <span data-ttu-id="cda6e-139">**\<SeeAlso cref="M:SomeClass.SomeMethod(System.String)" >**</span><span class="sxs-lookup"><span data-stu-id="cda6e-139">**\<seealso cref="M:SomeClass.SomeMethod(System.String)">**</span></span>  
 <span data-ttu-id="cda6e-140">**Zwróć uwagę na atrybut cref, aby odwołać określonej metody \</seealso >**</span><span class="sxs-lookup"><span data-stu-id="cda6e-140">**Notice the use of the cref attribute to reference a specific method \</seealso>**</span></span>  
 <span data-ttu-id="cda6e-141">**\</Member >**</span><span class="sxs-lookup"><span data-stu-id="cda6e-141">**\</member>**</span></span>  
 <span data-ttu-id="cda6e-142">**\<element członkowski name="M:SomeClass.Main(System.String[])" >**</span><span class="sxs-lookup"><span data-stu-id="cda6e-142">**\<member name="M:SomeClass.Main(System.String[])">**</span></span>  
 <span data-ttu-id="cda6e-143">**\<podsumowania >**</span><span class="sxs-lookup"><span data-stu-id="cda6e-143">**\<summary>**</span></span>  
 <span data-ttu-id="cda6e-144">**Punkt wejścia dla aplikacji.**</span><span class="sxs-lookup"><span data-stu-id="cda6e-144">**The entry point for the application.**</span></span>  
 <span data-ttu-id="cda6e-145">**\</ summary >**</span><span class="sxs-lookup"><span data-stu-id="cda6e-145">**\</summary>**</span></span>  
 <span data-ttu-id="cda6e-146">**\<param name = "args" > Lista argumentów wiersza polecenia\</param >**</span><span class="sxs-lookup"><span data-stu-id="cda6e-146">**\<param name="args"> A list of command line arguments\</param>**</span></span>  
 <span data-ttu-id="cda6e-147">**\</Member >**</span><span class="sxs-lookup"><span data-stu-id="cda6e-147">**\</member>**</span></span>  
 <span data-ttu-id="cda6e-148">**\<element członkowski name="P:SomeClass.Name" >**</span><span class="sxs-lookup"><span data-stu-id="cda6e-148">**\<member name="P:SomeClass.Name">**</span></span>  
 <span data-ttu-id="cda6e-149">**\<podsumowania >**</span><span class="sxs-lookup"><span data-stu-id="cda6e-149">**\<summary>**</span></span>  
 <span data-ttu-id="cda6e-150">**Nazwa właściwości  \< /summary >**</span><span class="sxs-lookup"><span data-stu-id="cda6e-150">**Name property \</summary>**</span></span>  
 <span data-ttu-id="cda6e-151">**\<wartość >**</span><span class="sxs-lookup"><span data-stu-id="cda6e-151">**\<value>**</span></span>  
 <span data-ttu-id="cda6e-152">**Wartość tagu jest używany do opisu wartość właściwości \< /value >**</span><span class="sxs-lookup"><span data-stu-id="cda6e-152">**A value tag is used to describe the property value\</value>**</span></span>  
 <span data-ttu-id="cda6e-153">**\</Member >**</span><span class="sxs-lookup"><span data-stu-id="cda6e-153">**\</member>**</span></span>  
 <span data-ttu-id="cda6e-154">**\</members >**</span><span class="sxs-lookup"><span data-stu-id="cda6e-154">**\</members>**</span></span>  
<span data-ttu-id="cda6e-155">**\</ doc >**</span><span class="sxs-lookup"><span data-stu-id="cda6e-155">**\</doc>**</span></span>   
## <a name="compiling-the-code"></a><span data-ttu-id="cda6e-156">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="cda6e-156">Compiling the Code</span></span>  
 <span data-ttu-id="cda6e-157">Aby skompilować w przykładzie, wpisz następujące polecenie w wierszu:</span><span class="sxs-lookup"><span data-stu-id="cda6e-157">To compile the example, type the following command line:</span></span>  
  
 `csc XMLsample.cs /doc:XMLsample.xml`  
  
 <span data-ttu-id="cda6e-158">Spowoduje to utworzenie pliku XML XMLsample.xml, które można wyświetlić w przeglądarce lub za pomocą polecenia typu.</span><span class="sxs-lookup"><span data-stu-id="cda6e-158">This will create the XML file XMLsample.xml, which you can view in your browser or by using the TYPE command.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="cda6e-159">Niezawodne programowanie</span><span class="sxs-lookup"><span data-stu-id="cda6e-159">Robust Programming</span></span>  
 <span data-ttu-id="cda6e-160">Plik dokumentacji XML rozpoczyna się od lokalizacje.</span><span class="sxs-lookup"><span data-stu-id="cda6e-160">XML documentation starts with ///.</span></span> <span data-ttu-id="cda6e-161">Podczas tworzenia nowego projektu kreatorów umieść starter lokalizacje wiersze w automatycznie.</span><span class="sxs-lookup"><span data-stu-id="cda6e-161">When you create a new project, the wizards put some starter /// lines in for you.</span></span> <span data-ttu-id="cda6e-162">Przetwarzanie komentarze ma pewne ograniczenia:</span><span class="sxs-lookup"><span data-stu-id="cda6e-162">The processing of these comments has some restrictions:</span></span>  
  
-   <span data-ttu-id="cda6e-163">Dokumentację musi być poprawnie sformułowanym XML.</span><span class="sxs-lookup"><span data-stu-id="cda6e-163">The documentation must be well-formed XML.</span></span> <span data-ttu-id="cda6e-164">Jeśli plik XML nie jest poprawnie sformułowany, generowania ostrzeżeń i pliku dokumentacji będzie zawierać komentarz z informacją, że wystąpił błąd podczas.</span><span class="sxs-lookup"><span data-stu-id="cda6e-164">If the XML is not well-formed, a warning is generated and the documentation file will contain a comment that says that an error was encountered.</span></span>  
  
-   <span data-ttu-id="cda6e-165">Deweloperzy mogą tworzyć własne zestawu tagów.</span><span class="sxs-lookup"><span data-stu-id="cda6e-165">Developers are free to create their own set of tags.</span></span> <span data-ttu-id="cda6e-166">Brak zalecanych zbiór znaczników (patrz sekcja dalsze informacje).</span><span class="sxs-lookup"><span data-stu-id="cda6e-166">There is a recommended set of tags (see the Further Reading section).</span></span> <span data-ttu-id="cda6e-167">Niektóre zalecane znaczniki mają specjalne znaczenie:</span><span class="sxs-lookup"><span data-stu-id="cda6e-167">Some of the recommended tags have special meanings:</span></span>  
  
    -   <span data-ttu-id="cda6e-168">\<Param > tag jest używany do opisywania parametrów.</span><span class="sxs-lookup"><span data-stu-id="cda6e-168">The \<param> tag is used to describe parameters.</span></span> <span data-ttu-id="cda6e-169">Jeśli używana, kompilator sprawdza, czy parametr istnieje i że wszystkie parametry są opisane w dokumentacji.</span><span class="sxs-lookup"><span data-stu-id="cda6e-169">If used, the compiler will verify that the parameter exists and that all parameters are described in the documentation.</span></span> <span data-ttu-id="cda6e-170">Jeśli weryfikacja nie powiodła się, kompilator generuje ostrzeżenie.</span><span class="sxs-lookup"><span data-stu-id="cda6e-170">If the verification failed, the compiler issues a warning.</span></span>  
  
    -   <span data-ttu-id="cda6e-171">`cref` Atrybut może zostać dołączony do żadnych znacznik w celu zapewnienia odwołania do elementu kodu.</span><span class="sxs-lookup"><span data-stu-id="cda6e-171">The `cref` attribute can be attached to any tag to provide a reference to a code element.</span></span> <span data-ttu-id="cda6e-172">Kompilator będzie Sprawdź, czy istnieje tego elementu kodu.</span><span class="sxs-lookup"><span data-stu-id="cda6e-172">The compiler will verify that this code element exists.</span></span> <span data-ttu-id="cda6e-173">Jeśli weryfikacja nie powiodła się, kompilator generuje ostrzeżenie.</span><span class="sxs-lookup"><span data-stu-id="cda6e-173">If the verification failed, the compiler issues a warning.</span></span> <span data-ttu-id="cda6e-174">Kompilator szanuje żadnego `using` instrukcje podczas wyszukiwania typu opisanego w `cref` atrybutu.</span><span class="sxs-lookup"><span data-stu-id="cda6e-174">The compiler respects any `using` statements when it looks for a type described in the `cref` attribute.</span></span>  
  
    -   <span data-ttu-id="cda6e-175">\<Podsumowania > tag jest używany przez funkcję IntelliSense w programie Visual Studio, aby wyświetlić dodatkowe informacje na temat typu lub elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="cda6e-175">The \<summary> tag is used by IntelliSense inside Visual Studio to display additional information about a type or member.</span></span>  
  
        > [!NOTE]
        >  <span data-ttu-id="cda6e-176">Plik XML nie zapewnia pełne informacje dotyczące typu i elementów członkowskich (na przykład go nie zawiera żadnych informacji o typie).</span><span class="sxs-lookup"><span data-stu-id="cda6e-176">The XML file does not provide full information about the type and members (for example, it does not contain any type information).</span></span> <span data-ttu-id="cda6e-177">Aby uzyskać pełne informacje dotyczące typu lub elementu członkowskiego, plik dokumentacji musi być używany razem odbicia na rzeczywisty typ lub element członkowski.</span><span class="sxs-lookup"><span data-stu-id="cda6e-177">To get full information about a type or member, the documentation file must be used together with reflection on the actual type or member.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cda6e-178">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="cda6e-178">See Also</span></span>  
 [<span data-ttu-id="cda6e-179">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="cda6e-179">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="cda6e-180">/ doc (opcje kompilatora C#)</span><span class="sxs-lookup"><span data-stu-id="cda6e-180">/doc (C# Compiler Options)</span></span>](../../../csharp/language-reference/compiler-options/doc-compiler-option.md)  
 [<span data-ttu-id="cda6e-181">Komentarze dokumentacji XML</span><span class="sxs-lookup"><span data-stu-id="cda6e-181">XML Documentation Comments</span></span>](../../../csharp/programming-guide/xmldoc/xml-documentation-comments.md)
