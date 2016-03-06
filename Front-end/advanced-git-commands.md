# ֱ�������ã�10�γ����õ�Git�����д���


>    �������Ѿ�ʹ��Git�ܳ�һ��ʱ���ˣ����Ƿ���һЩ���������Ŷӿ������Ǹ�����Ŀ�������õĸ߼�git���

## 1. ������һ���ύ�ĸı�
�������Ҿ���ʹ���� ����������û��ʹ��git�����������߼������޸ĵġ������������ύ���޸����ݵ�һ��zip�ļ��С�

```bash
git archive -o ../updated.zip HEAD $(git diff --name-only HEAD^)
```

## 2. ��������ύ��ĸı�
���Ƶģ��������Ҫ���ĳ�����ύ��ĸı�ʱ�������ʹ�������

```
git archive -o ../latest.zip NEW_COMMIT_ID_HERE $(git diff --name-only OLD_COMMIT_ID_HERE NEW_COMMIT_ID_HERE)
```

## 3. ��¡ ָ����Զ�̷�֧
��������ֻ��¡Զ�ֿ̲��һ��ָ����֧�������������ֿ��֧�����������ܴ�

```bash
git init
git remote add -t BRANCH_NAME_HERE -f origin REMOTE_REPO_URL_PATH_HERE
git checkout BRANCH_NAME_HERE
```

## 4. Ӧ�� �Ӳ���صı��زֿ����Ĳ���
�������Ҫ����һЩ����صı��زֿ���Ϊ�����ڲֿ�Ĳ������������ͨ������Ľݾ���

```bash
git --git-dir=PATH_TO_OTHER_REPOSITORY_HERE/.git format-patch -k -1 --stdout COMMIT_HASH_ID_HERE| git am -3 -k
```

## 5. ��� ��ķ�֧�ĸı��Ƿ�Ϊ������֧��һ����
cherry���������Ǽ����ķ�֧�ĸı��Ƿ����������һЩ��֧�С���ͨ��+����-��������ʾ�ӵ�ǰ��֧�������ķ�֧֮��ĸı䣺�Ƿ�ϲ���(merged)��.+ ָʾû�г�����������֧�У���֮��-�ͱ�ʾ�������������ķ�֧���ˡ�����������ȥ��⣺

```bash
git cherry -v OTHER_BRANCH_NAME_HERE
#For example: to check with master branch
git cherry -v master  <br>
```

## 6. ��ʼһ������ʷ���·�֧
��ʱ������Ҫ��ʼһ���·�֧�������ֲ���Ѻܳ��ܳ�����ʷ��¼�����������磬�����ڹ������򣨿�Դ��������Ĵ��룬�����ֲ������֪��������ʷ��¼��

```bash
git checkout --orphan NEW_BRANCH_NAME_HERE
```

## 7. ���л���֧�Ĵ�������֧Checkout�ļ�
�����л���֧�����������������֧�л������Ҫ���ļ���

```bash
git checkout BRANCH_NAME_HERE -- PATH_TO_FILE_IN_BRANCH_HERE
```

## 8. ������׷���ļ��ı䶯

���������һ���Ŷ��й��������Ҵ�Ҷ���ͬһ��branch���湤������ô�����п��ܻᾭ���õ�fetch��merge��������ʱ���������������Ļ��������ļ�����˵Ļ������͵���ÿ��merge���޸�����ʹ����һ���������Ҫ��git����ָ���ļ��ı䶯���������»�����merge�Ļ�������ļ��Ͳ��ᱻ�޸��ˡ�

```bash
git update-index --assume-unchanged PATH_TO_FILE_HERE
```

## 9. ����ύ�ı䶯�Ƿ���release��һ����

name-rev�����ܸ�����һ��commit��������һ��release��λ�á�ʹ������������Ϳ��Լ�����������ĸĶ��Ƿ���release��һ�����ˡ�

```bash
git name-rev --name-only COMMIT_HASH_HERE
```

## 10. ʹ��rebase���Ͷ���merge

����������Ŷ��й������������ŶӶ���ͬһ��branch���湤������ô���͵þ����ؽ���fetch/merge����pull��Git�У���֧�ĺϲ������ύ��merge����¼���Դ˱���һ��feature��֧��ʱ������֧�ϲ��������ڶ��Ŷӳ�Ա��ͬ������һ��branch�������У������merge�ᵼ��log�г��ֶ�����Ϣ���Ӷ�������������ˣ���������pull��ʱ��ʹ��rebase���Դ����������õ�merge��Ϣ���Ӷ�������ʷ��¼��������

```bash
git pull --rebase
```

��Ҳ���Խ�ĳ��branch����Ϊ����ʹ��rebase���ͣ�

```bash
git config branch.BRANCH_NAME_HERE.rebase true
```

Ӣ�ĳ��ԣ� [Webdeveloperplus](http://webdeveloperplus.com/general/10-useful-advanced-git-commands/)

�����������ԣ�[OSChina](http://www.oschina.net/translate/10-useful-advanced-git-commands)
