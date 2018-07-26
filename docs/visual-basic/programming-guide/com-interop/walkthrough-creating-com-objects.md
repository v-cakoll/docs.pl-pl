---
title: 'Wskazówki: tworzenie obiektów COM z Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- COM interop [Visual Basic], creating COM objects
- COM objects, creating
- COM interop [Visual Basic], walkthroughs
- object creation [Visual Basic], COM objects
- COM objects, walkthroughs
ms.assetid: 7b07a463-bc72-4392-9ba0-9dfcb697a44f
ms.openlocfilehash: caf0a071d65746f1027052e648ade538d62dc4bb
ms.sourcegitcommit: 70c76a12449439bac0f7a359866be5a0311ce960
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/25/2018
ms.locfileid: "39245690"
---
# <a name="walkthrough-creating-com-objects-with-visual-basic"></a>Wskazówki: tworzenie obiektów COM z Visual Basic
Podczas tworzenia nowych aplikacji lub składników, najlepiej utworzyć zestawów .NET Framework. Jednakże Visual Basic również ułatwia udostępnianie składników .NET Framework, dla modelu COM. Dzięki temu można zapewnić nowych składników dla starszych zestawów aplikacji, które wymagają składników COM. W tym instruktażu przedstawiono sposób użycia języka Visual Basic do udostępnienia [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] obiekty jako obiekty COM, zarówno z i bez szablonu klasy COM.  
  
 Najprostszym sposobem udostępnienia obiektów COM jest przy użyciu szablonu klasy COM. Szablon klasy COM tworzy nową klasę, a następnie konfiguruje projekt, aby wygenerować klasę i współdziałanie warstwy jako obiekt COM i zarejestruj je przy użyciu systemu operacyjnego.  
  
> [!NOTE]
>  Chociaż można także udostępnić klasy utworzone w języku Visual Basic jako obiekt COM dla niezarządzanego kodu do użycia, nie jest obiektem COM wartość true i nie można użyć w języku Visual Basic. Aby uzyskać więcej informacji, zobacz [współdziałanie COM w aplikacjach .NET Framework](../../../visual-basic/programming-guide/com-interop/com-interoperability-in-net-framework-applications.md).  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-create-a-com-object-by-using-the-com-class-template"></a>Aby utworzyć obiekt COM za pomocą szablonu klasy modelu COM  
  
1.  Otwórz nowy projekt aplikacji Windows z **pliku** menu, klikając **nowy projekt**.  
  
2.  W **nowy projekt** okno dialogowe, w obszarze **typów projektów** pola, należy sprawdzić, czy wybrano Windows. Wybierz **biblioteki klas** z **szablony** listy, a następnie kliknij przycisk **OK**. Zostanie wyświetlony nowy projekt.  
  
3.  Wybierz **Dodaj nowy element** z **projektu** menu. **Dodaj nowy element** zostanie wyświetlone okno dialogowe.  
  
4.  Wybierz **klasa COM —** z **szablony** listy, a następnie kliknij przycisk **Dodaj**. Visual Basic dodaje nową klasę i konfiguruje nowy projekt dla współdziałania z modelem COM.  
  
5.  Dodaj kod, takie jak właściwości, metody i zdarzenia do klasy COM.  
  
6.  Wybierz **kompilacji ClassLibrary1** z **kompilacji** menu. Visual Basic kompilacji zestawu i rejestruje obiekt COM w systemie operacyjnym.  
  
## <a name="creating-com-objects-without-the-com-class-template"></a>Tworzenie obiektów COM bez szablonu klasy modelu COM  
 Można również utworzyć klasę modelu COM ręcznie, zamiast używać szablonu klasy COM. Ta procedura jest pomocna podczas pracy z poziomu wiersza polecenia, lub gdy chcesz mieć większą kontrolę nad jak obiekty COM są zdefiniowane.  
  
#### <a name="to-set-up-your-project-to-generate-a-com-object"></a>Aby skonfigurować projekt do wygenerowania obiektów COM  
  
1.  Otwórz nowy projekt aplikacji Windows z **pliku** menu, klikając **NewProject**.  
  
2.  W **nowy projekt** okno dialogowe, w obszarze **typów projektów** pola, należy sprawdzić, czy wybrano Windows. Wybierz **biblioteki klas** z **szablony** listy, a następnie kliknij przycisk **OK**. Zostanie wyświetlony nowy projekt.  
  
3.  W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy projekt, a następnie kliknij przycisk **właściwości**. **Projektanta projektu** jest wyświetlana.  
  
4.  Kliknij przycisk **skompilować** kartę.  
  
5.  Wybierz **Zarejestruj dla współdziałania COM** pole wyboru.  
  
#### <a name="to-set-up-the-code-in-your-class-to-create-a-com-object"></a>Aby skonfigurować kod w swojej klasie, można utworzyć obiektu COM  
  
1.  W **Eksploratora rozwiązań**, kliknij dwukrotnie **Class1.vb** do wyświetlenia jego kodu.  
  
2.  Zmień nazwę klasy, która ma `ComClass1`.  
  
3.  Dodaj następujące stałe do `ComClass1`. Będą one przechowywane w stałych Unikatowy identyfikator globalny (GUID), które obiekty COM są wymagane do.  
  
     [!code-vb[VbVbalrInterop#2](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-creating-com-objects_1.vb)]  
  
4.  Na **narzędzia** menu, kliknij przycisk **Utwórz Guid**. W **Utwórz GUID** okno dialogowe, kliknij przycisk **Format rejestru** a następnie kliknij przycisk **kopiowania**. Kliknij przycisk **zakończenia**.  
  
5.  Zastąp ciąg pusty dla `ClassId` przy użyciu identyfikatora GUID, nawiasy klamrowe usuwanie wiodące i końcowe. Na przykład, jeśli identyfikator GUID udostępnione przez Guidgen jest `"{2C8B0AEE-02C9-486e-B809-C780A11530FE}"` , a następnie kod powinien wyglądać następująco.  
  
     [!code-vb[VbVbalrInterop#3](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-creating-com-objects_2.vb)]  
  
6.  Powtórz poprzednie kroki dla `InterfaceId` i `EventsId` stałych, jak w poniższym przykładzie.  
  
     [!code-vb[VbVbalrInterop#4](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-creating-com-objects_3.vb)]  
  
    > [!NOTE]
    >  Upewnij się, że identyfikator GUID w faktycznej nowych i unikatowych; w przeciwnym razie składnika COM mogą powodować konflikt z innymi składnikami COM.  
  
7.  Dodaj `ComClass` atrybutu `ComClass1`, określając identyfikatorów GUID dla Identyfikatora klasy, identyfikator interfejsu i identyfikator zdarzenia, jak w poniższym przykładzie:  
  
     [!code-vb[VbVbalrInterop#5](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-creating-com-objects_4.vb)]  
  
8.  Klasy COM musi mieć bez parametrów `Public Sub New()` konstruktora lub klasa nie zarejestruje poprawnie. Dodaj konstruktor bez parametrów do klasy:  
  
     [!code-vb[VbVbalrInterop#6](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-creating-com-objects_5.vb)]  
  
9. Dodaj do klasy, kończy go za pomocą właściwości, metody i zdarzenia `End Class` instrukcji. Wybierz **Kompiluj rozwiązanie** z **kompilacji** menu. Visual Basic kompilacji zestawu i rejestruje obiekt COM w systemie operacyjnym.  
  
    > [!NOTE]
    >  Nie można użyć obiektów COM, który można wygenerować za pomocą Visual Basic przez inne aplikacje w języku Visual Basic, ponieważ nie mają wartość true, obiekty COM. Próby dodania odwołania do tych obiektów COM zgłosi błąd. Aby uzyskać więcej informacji, zobacz [współdziałanie COM w aplikacjach .NET Framework](../../../visual-basic/programming-guide/com-interop/com-interoperability-in-net-framework-applications.md).  
  
## <a name="see-also"></a>Zobacz też  
 <xref:Microsoft.VisualBasic.ComClassAttribute>  
 [Usługa międzyoperacyjna modelu COM](../../../visual-basic/programming-guide/com-interop/index.md)  
 [Przewodnik: wdrażanie dziedziczenia z obiektami COM](../../../visual-basic/programming-guide/com-interop/walkthrough-implementing-inheritance-with-com-objects.md)  
 [#Region, dyrektywa](../../../visual-basic/language-reference/directives/region-directive.md)  
 [Współdziałanie COM w aplikacjach .NET Framework](../../../visual-basic/programming-guide/com-interop/com-interoperability-in-net-framework-applications.md)  
 [Rozwiązywanie problemów związanych z współdziałaniem](../../../visual-basic/programming-guide/com-interop/troubleshooting-interoperability.md)
