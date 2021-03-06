---
redirect_url: /visualstudio/csharp-ide/refactoring/encapsulate-field
title: "Encapsulate Field Refactoring (C#) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "Encapsulate Field refactoring operation [C#]"
  - "refactoring [C#], Encapsulate Field"
ms.assetid: bf714a04-ab1e-49ce-99ce-dda1ebb1a17f
caps.latest.revision: 26
author: "gewarren"
ms.author: "gewarren"
manager: "ghogen"
---
# Encapsulate Field Refactoring (C#)
The **Encapsulate Field** refactoring operation enables you to quickly create a property from an existing field, and then seamlessly update your code with references to the new property.  
  
 When a [field](/dotnet/csharp/programming-guide/classes-and-structs/fields) is [public](/dotnet/csharp/language-reference/keywords/public), other objects have direct access to that field and can modify it, undetected by the object that owns that field. By using [properties](/dotnet/csharp/programming-guide/classes-and-structs/properties) to encapsulate that field, you can disallow direct access to fields.  
  
 To create the new property, the **Encapsulate Field** operation changes the access modifier for the field that you want to encapsulate to [private](/dotnet/csharp/language-reference/keywords/private), and then generates [get](/dotnet/csharp/language-reference/keywords/get) and [set](/dotnet/csharp/language-reference/keywords/set) accessors for that field. In some cases, only a `get` accessor is generated, such as when the field is declared read-only.  
  
 The refactoring engine updates your code with references to the new property in the areas specified in the **Update References** section of the **Encapsulate Field** dialog box.  
  
### To create a property from a field  
  
1.  Create a console application named `EncapsulateFieldExample`, and then replace `Program` with the following example code.  
  
    ```csharp  
    class Square  
    {  
        // Select the word 'width' and then use Encapsulate Field.  
        public int width, height;  
    }  
    class MainClass  
    {  
        public static void Main()  
        {  
            Square mySquare = new Square();  
            mySquare.width = 110;  
            mySquare.height = 150;  
            // Output values for width and height.  
            Console.WriteLine("width = {0}", mySquare.width);  
            Console.WriteLine("height = {0}", mySquare.height);  
        }  
    }  
    ```  
  
2.  In the [Code Editor](../ide/writing-code-in-the-code-and-text-editor.md), place the cursor in the declaration, on the name of the field that you want to encapsulate. In the example below, place the cursor on the word `width`:  
  
    ```csharp  
    public int width, height;  
    ```  
  
3.  On the **Refactor** menu, click **Encapsulate Field**.  
  
     The **Encapsulate Field** dialog box appears.  
  
     You can also type the keyboard shortcut CTRL+R, E to display the **Encapsulate Field** dialog box.  
  
     You can also right-click the cursor, point to **Refactor**, and then click **Encapsulate Field** to display the **Encapsulate Field** dialog box.  
  
4.  Specify settings.  
  
5.  Press ENTER, or click the **OK** button.  
  
6.  If you selected the **Preview reference changes** option, then the **Preview Reference Changes** window opens. Click the **Apply** button.  
  
     The following `get` and `set` accessor code is displayed in your source file:  
  
    ```csharp  
    public int Width  
    {  
        get { return width; }  
        set { width = value; }  
    }  
    ```  
  
     The code in the `Main` method is also updated to the new `Width` property name.  
  
    ```csharp  
    Square mySquare = new Square();  
    mySquare.Width = 110;  
    mySquare.height = 150;  
    // Output values for width and height.  
    Console.WriteLine("width = {0}", mySquare.Width);  
    ```  
  
## Remarks  
 The **Encapsulate Field** operation is only possible when the cursor is positioned on the same line as the field declaration.  
  
 For declarations that declare multiple fields, **Encapsulate Field** uses the comma as a boundary between fields, and initiates refactoring on the field that is nearest the cursor and on the same line as the cursor. You can also specify which field you want to encapsulate by selecting the name of that field in the declaration.  
  
 The code that is generated by this refactoring operation is modeled by the encapsulate field code snippets feature. Code Snippets are modifiable. For more information, see [Code Snippets](../ide/visual-csharp-code-snippets.md).  
  
## See Also  
 [Refactoring (C#)](refactoring-csharp.md)   
 [Visual C# Code Snippets](../ide/visual-csharp-code-snippets.md)