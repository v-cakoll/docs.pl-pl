---
title: tworzenie odbiorców dzienników niestandardowych
ms.date: 07/20/2015
helpviewer_keywords:
- custom log listeners
- My.Application.Log object, custom log listeners
ms.assetid: 0e019115-4b25-4820-afb1-af8c6e391698
ms.openlocfilehash: 7b611e93119dc66a9404cf271ea201676d7b5318
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74353624"
---
# <a name="walkthrough-creating-custom-log-listeners-visual-basic"></a><span data-ttu-id="68c38-102">Wskazówki: tworzenie odbiorników logu niestandardowego (C# i Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="68c38-102">Walkthrough: Creating Custom Log Listeners (Visual Basic)</span></span>

<span data-ttu-id="68c38-103">This walkthrough demonstrates how to create a custom log listener and configure it to listen to the output of the `My.Application.Log` object.</span><span class="sxs-lookup"><span data-stu-id="68c38-103">This walkthrough demonstrates how to create a custom log listener and configure it to listen to the output of the `My.Application.Log` object.</span></span>

## <a name="getting-started"></a><span data-ttu-id="68c38-104">Wprowadzenie</span><span class="sxs-lookup"><span data-stu-id="68c38-104">Getting Started</span></span>

<span data-ttu-id="68c38-105">Log listeners must inherit from the <xref:System.Diagnostics.TraceListener> class.</span><span class="sxs-lookup"><span data-stu-id="68c38-105">Log listeners must inherit from the <xref:System.Diagnostics.TraceListener> class.</span></span>

#### <a name="to-create-the-listener"></a><span data-ttu-id="68c38-106">To create the listener</span><span class="sxs-lookup"><span data-stu-id="68c38-106">To create the listener</span></span>

- <span data-ttu-id="68c38-107">In your application, create a class named `SimpleListener` that inherits from <xref:System.Diagnostics.TraceListener>.</span><span class="sxs-lookup"><span data-stu-id="68c38-107">In your application, create a class named `SimpleListener` that inherits from <xref:System.Diagnostics.TraceListener>.</span></span>

     [!code-vb[VbVbalrMyApplicationLog#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/Form1.vb#16)]

     <span data-ttu-id="68c38-108">The <xref:System.Diagnostics.TraceListener.Write%2A> and <xref:System.Diagnostics.TraceListener.WriteLine%2A> methods, required by the base class, call `MsgBox` to display their input.</span><span class="sxs-lookup"><span data-stu-id="68c38-108">The <xref:System.Diagnostics.TraceListener.Write%2A> and <xref:System.Diagnostics.TraceListener.WriteLine%2A> methods, required by the base class, call `MsgBox` to display their input.</span></span>

     <span data-ttu-id="68c38-109">The <xref:System.Security.Permissions.HostProtectionAttribute> attribute is applied to the <xref:System.Diagnostics.TraceListener.Write%2A> and <xref:System.Diagnostics.TraceListener.WriteLine%2A> methods so that their attributes match the base class methods.</span><span class="sxs-lookup"><span data-stu-id="68c38-109">The <xref:System.Security.Permissions.HostProtectionAttribute> attribute is applied to the <xref:System.Diagnostics.TraceListener.Write%2A> and <xref:System.Diagnostics.TraceListener.WriteLine%2A> methods so that their attributes match the base class methods.</span></span> <span data-ttu-id="68c38-110">The <xref:System.Security.Permissions.HostProtectionAttribute> attribute allows the host that runs the code to determine that the code exposes host-protection synchronization.</span><span class="sxs-lookup"><span data-stu-id="68c38-110">The <xref:System.Security.Permissions.HostProtectionAttribute> attribute allows the host that runs the code to determine that the code exposes host-protection synchronization.</span></span>

    > [!NOTE]
    > <span data-ttu-id="68c38-111">The <xref:System.Security.Permissions.HostProtectionAttribute> attribute is effective only on unmanaged applications that host the common language runtime and that implement host protection, such as SQL Server.</span><span class="sxs-lookup"><span data-stu-id="68c38-111">The <xref:System.Security.Permissions.HostProtectionAttribute> attribute is effective only on unmanaged applications that host the common language runtime and that implement host protection, such as SQL Server.</span></span>

<span data-ttu-id="68c38-112">To ensure that `My.Application.Log` uses your log listener, you should strongly name the assembly that contains your log listener.</span><span class="sxs-lookup"><span data-stu-id="68c38-112">To ensure that `My.Application.Log` uses your log listener, you should strongly name the assembly that contains your log listener.</span></span>

<span data-ttu-id="68c38-113">The next procedure provides some simple steps for creating a strongly named log-listener assembly.</span><span class="sxs-lookup"><span data-stu-id="68c38-113">The next procedure provides some simple steps for creating a strongly named log-listener assembly.</span></span> <span data-ttu-id="68c38-114">For more information, see [Creating and Using Strong-Named Assemblies](../../../../standard/assembly/create-use-strong-named.md).</span><span class="sxs-lookup"><span data-stu-id="68c38-114">For more information, see [Creating and Using Strong-Named Assemblies](../../../../standard/assembly/create-use-strong-named.md).</span></span>

#### <a name="to-strongly-name-the-log-listener-assembly"></a><span data-ttu-id="68c38-115">To strongly name the log-listener assembly</span><span class="sxs-lookup"><span data-stu-id="68c38-115">To strongly name the log-listener assembly</span></span>

1. <span data-ttu-id="68c38-116">Have a project selected in **Solution Explorer**.</span><span class="sxs-lookup"><span data-stu-id="68c38-116">Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="68c38-117">On the **Project** menu, choose **Properties**.</span><span class="sxs-lookup"><span data-stu-id="68c38-117">On the **Project** menu, choose **Properties**.</span></span>

2. <span data-ttu-id="68c38-118">Click the **Signing** tab.</span><span class="sxs-lookup"><span data-stu-id="68c38-118">Click the **Signing** tab.</span></span>

3. <span data-ttu-id="68c38-119">Select the **Sign the assembly** box.</span><span class="sxs-lookup"><span data-stu-id="68c38-119">Select the **Sign the assembly** box.</span></span>

4. <span data-ttu-id="68c38-120">Select **\<New>** from the **Choose a strong name key file** drop-down list.</span><span class="sxs-lookup"><span data-stu-id="68c38-120">Select **\<New>** from the **Choose a strong name key file** drop-down list.</span></span>

     <span data-ttu-id="68c38-121">The **Create Strong Name Key** dialog box opens.</span><span class="sxs-lookup"><span data-stu-id="68c38-121">The **Create Strong Name Key** dialog box opens.</span></span>

5. <span data-ttu-id="68c38-122">Provide a name for the key file in the **Key file name** box.</span><span class="sxs-lookup"><span data-stu-id="68c38-122">Provide a name for the key file in the **Key file name** box.</span></span>

6. <span data-ttu-id="68c38-123">Enter a password in the **Enter password** and **Confirm password** boxes.</span><span class="sxs-lookup"><span data-stu-id="68c38-123">Enter a password in the **Enter password** and **Confirm password** boxes.</span></span>

7. <span data-ttu-id="68c38-124">Kliknij przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="68c38-124">Click **OK**.</span></span>

8. <span data-ttu-id="68c38-125">Rebuild the application.</span><span class="sxs-lookup"><span data-stu-id="68c38-125">Rebuild the application.</span></span>

## <a name="adding-the-listener"></a><span data-ttu-id="68c38-126">Adding the Listener</span><span class="sxs-lookup"><span data-stu-id="68c38-126">Adding the Listener</span></span>

<span data-ttu-id="68c38-127">Now that the assembly has a strong name, you need to determine the strong name of the listener so that `My.Application.Log` uses your log listener.</span><span class="sxs-lookup"><span data-stu-id="68c38-127">Now that the assembly has a strong name, you need to determine the strong name of the listener so that `My.Application.Log` uses your log listener.</span></span>

<span data-ttu-id="68c38-128">The format of a strongly named type is as follows.</span><span class="sxs-lookup"><span data-stu-id="68c38-128">The format of a strongly named type is as follows.</span></span>

<span data-ttu-id="68c38-129">\<type name>, \<assembly name>, \<version number>, \<culture>, \<strong name></span><span class="sxs-lookup"><span data-stu-id="68c38-129">\<type name>, \<assembly name>, \<version number>, \<culture>, \<strong name></span></span>

#### <a name="to-determine-the-strong-name-of-the-listener"></a><span data-ttu-id="68c38-130">To determine the strong name of the listener</span><span class="sxs-lookup"><span data-stu-id="68c38-130">To determine the strong name of the listener</span></span>

- <span data-ttu-id="68c38-131">The following code shows how to determine the strongly named type name for `SimpleListener`.</span><span class="sxs-lookup"><span data-stu-id="68c38-131">The following code shows how to determine the strongly named type name for `SimpleListener`.</span></span>

     [!code-vb[VbVbalrMyApplicationLog#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/Form1.vb#17)]

     <span data-ttu-id="68c38-132">The strong name of the type depends on your project.</span><span class="sxs-lookup"><span data-stu-id="68c38-132">The strong name of the type depends on your project.</span></span>

<span data-ttu-id="68c38-133">With the strong name, you can add the listener to the `My.Application.Log` log-listener collection.</span><span class="sxs-lookup"><span data-stu-id="68c38-133">With the strong name, you can add the listener to the `My.Application.Log` log-listener collection.</span></span>

#### <a name="to-add-the-listener-to-myapplicationlog"></a><span data-ttu-id="68c38-134">To add the listener to My.Application.Log</span><span class="sxs-lookup"><span data-stu-id="68c38-134">To add the listener to My.Application.Log</span></span>

1. <span data-ttu-id="68c38-135">Right-click on app.config in the **Solution Explorer** and choose **Open**.</span><span class="sxs-lookup"><span data-stu-id="68c38-135">Right-click on app.config in the **Solution Explorer** and choose **Open**.</span></span>

     <span data-ttu-id="68c38-136">—lub—</span><span class="sxs-lookup"><span data-stu-id="68c38-136">-or-</span></span>

     <span data-ttu-id="68c38-137">If there is an app.config file:</span><span class="sxs-lookup"><span data-stu-id="68c38-137">If there is an app.config file:</span></span>

    1. <span data-ttu-id="68c38-138">On the **Project** menu, choose **Add New Item**.</span><span class="sxs-lookup"><span data-stu-id="68c38-138">On the **Project** menu, choose **Add New Item**.</span></span>

    2. <span data-ttu-id="68c38-139">From the **Add New Item** dialog box, choose **Application Configuration File**.</span><span class="sxs-lookup"><span data-stu-id="68c38-139">From the **Add New Item** dialog box, choose **Application Configuration File**.</span></span>

    3. <span data-ttu-id="68c38-140">Kliknij przycisk **Dodaj**.</span><span class="sxs-lookup"><span data-stu-id="68c38-140">Click **Add**.</span></span>

2. <span data-ttu-id="68c38-141">Locate the `<listeners>` section, in the `<source>` section with the `name` attribute "DefaultSource", located in the `<sources>` section.</span><span class="sxs-lookup"><span data-stu-id="68c38-141">Locate the `<listeners>` section, in the `<source>` section with the `name` attribute "DefaultSource", located in the `<sources>` section.</span></span> <span data-ttu-id="68c38-142">The `<sources>` section is located in the `<system.diagnostics>` section, in the top-level `<configuration>` section.</span><span class="sxs-lookup"><span data-stu-id="68c38-142">The `<sources>` section is located in the `<system.diagnostics>` section, in the top-level `<configuration>` section.</span></span>

3. <span data-ttu-id="68c38-143">Add this element to the `<listeners>` section:</span><span class="sxs-lookup"><span data-stu-id="68c38-143">Add this element to the `<listeners>` section:</span></span>

    ```xml
    <add name="SimpleLog" />
    ```

4. <span data-ttu-id="68c38-144">Locate the `<sharedListeners>` section, in the `<system.diagnostics>` section, in the top-level `<configuration>` section.</span><span class="sxs-lookup"><span data-stu-id="68c38-144">Locate the `<sharedListeners>` section, in the `<system.diagnostics>` section, in the top-level `<configuration>` section.</span></span>

5. <span data-ttu-id="68c38-145">Add this element to that `<sharedListeners>` section:</span><span class="sxs-lookup"><span data-stu-id="68c38-145">Add this element to that `<sharedListeners>` section:</span></span>

    ```xml
    <add name="SimpleLog" type="SimpleLogStrongName" />
    ```

     <span data-ttu-id="68c38-146">Change the value of `SimpleLogStrongName` to be the strong name of the listener.</span><span class="sxs-lookup"><span data-stu-id="68c38-146">Change the value of `SimpleLogStrongName` to be the strong name of the listener.</span></span>

## <a name="see-also"></a><span data-ttu-id="68c38-147">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="68c38-147">See also</span></span>

- <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>
- [<span data-ttu-id="68c38-148">Praca z dziennikami aplikacji</span><span class="sxs-lookup"><span data-stu-id="68c38-148">Working with Application Logs</span></span>](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md)
- [<span data-ttu-id="68c38-149">Instrukcje: wyjątki dziennika</span><span class="sxs-lookup"><span data-stu-id="68c38-149">How to: Log Exceptions</span></span>](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-exceptions.md)
- [<span data-ttu-id="68c38-150">Instrukcje: zapisywanie komunikatów dziennika</span><span class="sxs-lookup"><span data-stu-id="68c38-150">How to: Write Log Messages</span></span>](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-log-messages.md)
- [<span data-ttu-id="68c38-151">Przewodnik: zmienianie lokalizacji, w której My.Application.Log zapisuje informacje</span><span class="sxs-lookup"><span data-stu-id="68c38-151">Walkthrough: Changing Where My.Application.Log Writes Information</span></span>](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-changing-where-my-application-log-writes-information.md)
