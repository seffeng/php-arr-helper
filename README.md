## PHP Helpers

### 安装

```shell
# 安装
$ composer require seffeng/arr-helper
```

### 目录说明

```
|---src
|   |   Arr.php
|   |   ReplaceArrayValue.php
|   |   UnsetArrayValue.php
|   |---Traits
|           ArrTrait.php
|---tests
|       ArrTest.php
```

### 示例

```php
/**
 * TestController.php
 * 示例
 */
namespace App\Http\Controllers;

use Seffeng\ArrHelper\Arr;
use Seffeng\ArrHelper\ReplaceArrayValue;

class TestController extends Controller
{
    public function index()
    {
        $arr = [
            'a' => [
                'b' => [
                    'c' => 'ccc'
                ]
            ],
            'd' => [
                'b' => 'ccc',
                'e' => [
                    'f' => 'hhh'
                ]
            ]
        ];
        echo '<pre>';
        var_dump(Arr::getValue($arr, 'a.b.c', ''));
        var_dump(Arr::getDepth($arr));
        print_r(Arr::getColumn($arr, 'b'));
        print_r($arr);
        print_r(Arr::merge($arr, [
            'd' => new ReplaceArrayValue(['hhh' => 'iii']),
            'i' => [
                'j' => 'kkk'
            ]
        ]));
    }
}
```

### 备注

1、更多示例请参考 tests 目录下测试文件。